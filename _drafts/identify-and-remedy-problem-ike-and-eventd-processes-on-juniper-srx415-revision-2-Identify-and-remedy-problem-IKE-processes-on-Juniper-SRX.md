---
id: 420
title: Identify and remedy problem IKE processes on Juniper SRX
date: 2013-02-02T12:31:21-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2013/02/415-revision-2/
permalink: /2013/02/415-revision-2/
---
Recently we encountered a very strange behavior on an SRX 5800 cluster.  The cluster, which is in active/active mode, started dropping OSPF adjacencies to it&#8217;s neighboring routing equipment, in this case, Juniper MX480 and Brocade/Foundry MLX8.  Strange behavior indeed, since for us, these had been rock solid for around 2 years and we&#8217;d never seen this odd behavior before.

Honestly, we started looking at the routers first since this was something the SRX has never done before.  After noticing that it was actually link dropping and not just OSPF having issues, we dug deeper into logs (as an aside, this is an **excellent** reason to centrally syslog everything.  And I do mean <span style="text-decoration: underline;"><strong>everything</strong></span>).  To our surprise and dismay, it was actually the SRX node0 actually rebooting all of its interface line cards.

&#8220;_show chassis routing-engine_&#8221; showed that User was taking up a very significant amount of CPU.  This is a problem.

[<img class="aligncenter size-full wp-image-416" alt="Screen Shot 2013-02-01 at 10.37.27 AM" src="http://www.forwardingplane.net/wp-content/uploads/2013/02/Screen-Shot-2013-02-01-at-10.37.27-AM.png" width="586" height="625" srcset="http://www.forwardingplane.net/wp-content/uploads/2013/02/Screen-Shot-2013-02-01-at-10.37.27-AM.png 586w, http://www.forwardingplane.net/wp-content/uploads/2013/02/Screen-Shot-2013-02-01-at-10.37.27-AM-281x300.png 281w, http://www.forwardingplane.net/wp-content/uploads/2013/02/Screen-Shot-2013-02-01-at-10.37.27-AM-550x586.png 550w" sizes="(max-width: 586px) 100vw, 586px" />](http://www.forwardingplane.net/wp-content/uploads/2013/02/Screen-Shot-2013-02-01-at-10.37.27-AM.png)

&nbsp;

As you can probably guess, this isn&#8217;t a good state.  So, in order to drill down what was causing User to be so abnormally high, we had to do a little sleuthing.  Running &#8220;_show system processes extensive | except 0.00_&#8221; will display any process that isn&#8217;t zero.  From here it was pretty obvious what was eating the CPU.

[<img class="aligncenter size-full wp-image-417" alt="Screen Shot 2013-02-01 at 10.43.50 AM" src="http://www.forwardingplane.net/wp-content/uploads/2013/02/Screen-Shot-2013-02-01-at-10.43.50-AM.png" width="581" height="365" srcset="http://www.forwardingplane.net/wp-content/uploads/2013/02/Screen-Shot-2013-02-01-at-10.43.50-AM.png 581w, http://www.forwardingplane.net/wp-content/uploads/2013/02/Screen-Shot-2013-02-01-at-10.43.50-AM-300x188.png 300w, http://www.forwardingplane.net/wp-content/uploads/2013/02/Screen-Shot-2013-02-01-at-10.43.50-AM-550x345.png 550w" sizes="(max-width: 581px) 100vw, 581px" />](http://www.forwardingplane.net/wp-content/uploads/2013/02/Screen-Shot-2013-02-01-at-10.43.50-AM.png)

&nbsp;

&#8220;kmd&#8221; and &#8220;eventd&#8221;, as you can see, are chewing up an abnormally high amount of CPU.  First things first, make sure no traceoptions are on.

&#8220;_show conf | display set | match traceoptions_&#8221;  We had some on so we disabled them.  Next, lets make sure we know what &#8220;kid&#8221; and &#8220;eventd&#8221; are.

<a href="http://www.juniper.net/techpubs/software/junos/junos94/syslog-messages/kmd-system-log-messages.html" target="_blank">KMD</a> is the key management process. It provides IP Security (IPSec) authentication services for encryption Physical Interface Cards (PICs).

<a href="http://www.juniper.net/techpubs/en_US/junos10.1/information-products/topic-collections/syslog-messages/jd0e22130.html" target="_blank">eventd</a> is the event policy process. It performs configured actions in response to events on a routing platform that trigger system log messages.

It&#8217;s all starting to add up.  I&#8217;ll bet there are a LOT of IPsec messeges in the log.

&#8220;_show log messages_&#8221; confirms this.  There are a LOT of KMD messages, which is likely causing events to eat even more resources to generate them.

_Jan 29 12:02:53 fw1 (FPC Slot 11, PIC Slot 0) init: kmd1 (PID 176) started_  
_Jan 29 12:02:53 _fw1_ (FPC Slot 11, PIC Slot 0) init: kmd2 (PID 177) started_  
_Jan 29 12:02:53 _fw1_ (FPC Slot 11, PIC Slot 0) init: kmd3 (PID 178) started_  
_Jan 29 12:02:53 _fw1_ (FPC Slot 11, PIC Slot 0) init: kmd4 (PID 179) started_  
_Jan 29 12:02:54 _fw1_ (FPC Slot 11, PIC Slot 1) init: kmd1 (PID 176) started_  
_Jan 29 12:02:55 _fw1_ (FPC Slot 11, PIC Slot 1) init: kmd2 (PID 177) started_  
_Jan 29 12:02:55 _fw1_ (FPC Slot 11, PIC Slot 1) init: kmd3 (PID 178) started_  
_Jan 29 12:02:55 _fw1_ (FPC Slot 11, PIC Slot 1) init: kmd4 (PID 180) started_  
_Jan 29 12:03:13 _fw1_ (FPC Slot 4, PIC Slot 0) init: kmd1 (PID 176) started_  
_Jan 29 12:03:13 _fw1_ (FPC Slot 4, PIC Slot 0) init: kmd2 (PID 177) started_  
_Jan 29 12:03:13 _fw1_ (FPC Slot 4, PIC Slot 0) init: kmd3 (PID 178) started_  
_Jan 29 12:03:13 _fw1_ (FPC Slot 4, PIC Slot 0) init: kmd4 (PID 179) started_  
_Jan 29 12:03:14 _fw1_ (FPC Slot 5, PIC Slot 0) init: kmd1 (PID 176) started_  
_Jan 29 12:03:14 _fw1_ (FPC Slot 5, PIC Slot 0) init: kmd2 (PID 177) started_  
_Jan 29 12:03:14 _fw1_ (FPC Slot 5, PIC Slot 0) init: kmd3 (PID 178) started_  
_Jan 29 12:03:15 _fw1_ (FPC Slot 5, PIC Slot 0) init: kmd4 (PID 179) started_

&nbsp;

Check the security log to verify &#8220;_show log kmed_&#8221;

_Dec 27 05:58:05 KMD\_INTERNAL\_ERROR: iked\_re\_ipc\_err\_handler: status: 1: usp\_ipc\_client_open: failed to connect to the server after 5 retries  
Dec 27 05:58:05 KMD\_INTERNAL\_ERROR: iked\_re\_send\_msg\_to\_spu: failed to connect to iked\_spu on SPU &#8211; Connection refused.  
Dec 27 05:58:05 KMD\_INTERNAL\_ERROR: iked\_re\_ipc\_err\_handler: status: 1: usp\_ipc\_client_open: failed to connect to the server after 5 retries  
Dec 27 05:58:05 KMD\_INTERNAL\_ERROR: iked\_re\_send\_msg\_to\_spu: failed to connect to iked\_spu on SPU &#8211; Connection refused.  
Dec 27 05:58:05 KMD\_INTERNAL\_ERROR: iked\_re\_ipc\_err\_handler: status: 1: usp\_ipc\_client_open: failed to connect to the server after 5 retries  
Dec 27 05:58:05 KMD\_INTERNAL\_ERROR: iked\_re\_send\_msg\_to\_spu: failed to connect to iked\_spu on SPU &#8211; Connection refused.  
Dec 27 05:58:05 KMD\_INTERNAL\_ERROR: iked\_re\_ipc\_err\_handler: status: 1: usp\_ipc\_client_open: failed to connect to the server after 5 retries  
Dec 27 05:58:05 KMD\_INTERNAL\_ERROR: iked\_re\_send\_msg\_to\_spu: failed to connect to iked\_spu on SPU &#8211; Connection refused.  
Dec 27 05:58:05 KMD\_INTERNAL\_ERROR: iked\_re\_ipc\_err\_handler: status: 1: usp\_ipc\_client_open: failed to connect to the server after 5 retries_

&nbsp;

Yeah, looks suspicious.  Lets restart ipsec-key-management and see if that helps.

&#8220;_restart ipsec-key-management&#8221;.  _

**_Note: If this does not work, you may have to drop to the shell and kill it like a unix process.  _**

_&#8220;start shell&#8221;_**_  _**

**__**<em id="__mceDel">&#8220;kill -9 kmd&#8221;</em>

Idle process should now be back to normal.

[<img class="aligncenter size-full wp-image-419" alt="Screen Shot 2013-02-02 at 12.24.11 PM" src="http://www.forwardingplane.net/wp-content/uploads/2013/02/Screen-Shot-2013-02-02-at-12.24.11-PM.png" width="591" height="444" srcset="http://www.forwardingplane.net/wp-content/uploads/2013/02/Screen-Shot-2013-02-02-at-12.24.11-PM.png 591w, http://www.forwardingplane.net/wp-content/uploads/2013/02/Screen-Shot-2013-02-02-at-12.24.11-PM-300x225.png 300w, http://www.forwardingplane.net/wp-content/uploads/2013/02/Screen-Shot-2013-02-02-at-12.24.11-PM-550x413.png 550w" sizes="(max-width: 591px) 100vw, 591px" />](http://www.forwardingplane.net/wp-content/uploads/2013/02/Screen-Shot-2013-02-02-at-12.24.11-PM.png)

&nbsp;

CPU&#8217;s were at a &#8220;normal&#8221; state in our environment has the idle process near 90% (+/-).  In the future this will be monitored so that this problem does sneak up on us.

Now, the right way to remedy this is to disable those services if you don&#8217;t need them.  If you do not plan to terminate VPN tunnels, there is no reason to run the services (on by default) to do so.  We opted to both disable and do a more inclusive loopback filter which seems to have taken care of the problem.

&nbsp;

Take aways from this is multi faceted.  The SRX is a weird beast It&#8217;s JunOs, so the inclination is to treat it like a router, but it &#8216;s not.  It&#8217;s a firewall.  I&#8217;m planning to write up an &#8220;SRX command cheat sheet&#8221; for this because it&#8217;s got enough different pieces and commands that I believe it warrants one.  Secondly, there are a lot of intracacies in monitoring these devices since they arent just routers.  I&#8217;m hoping to come up with a best practice for monitiring an SRX cluster in a carrier type environment as well.  I&#8217;m sure they&#8217;ll both be living documents.

&nbsp;

&nbsp;