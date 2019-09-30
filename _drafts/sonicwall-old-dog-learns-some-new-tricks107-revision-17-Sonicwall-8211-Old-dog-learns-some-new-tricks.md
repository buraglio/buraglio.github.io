---
id: 134
title: 'Sonicwall &#8211; Old dog learns [some] new tricks'
date: 2012-12-07T17:03:04-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2012/12/107-revision-17/
permalink: /2012/12/107-revision-17/
---
~12 years ago I had a drinking buddy that worked with me at the regional ISP.   We had a lot in common, he had been an icon back in the [didjits](http://en.wikipedia.org/wiki/The_Didjits) era of punk rock in Champaign Urbana and we had briefly been in a terrible band together.  He introduced me to a dude that to this day I just knew as &#8220;Ravi Sonicwall&#8221;.  He had apparently been recruited from the U of I, written a lot of the low level pieces of the original sonicwall and retired to enjoy life and buy beers (he actually scolded me at a bar for buying him a beer saying &#8220;when I&#8217;m in town, I buy the beers&#8221;).

I had purchased a few sonicwall boxes after that, having only really used linux, IOS, checkpoint on nokia boxes and *_shudder_* Novell Border manager.  I liked the boxes since they had a GUI and I could hand off day-to-day operations to someone that !=Me.  After a year or so in production, I started to become frustrated with them,  the ones I had lacked a CLI completely and had fallen behind on the things I needed to do with them.   Their cost to feature wasn&#8217;t there for what I needed and the ones I had purchased systematically had hardware failures all within 7 months.  I wrote off sonicwall completely at that point.

Fast forward a decade.

Sonicwall purchased by Dell.

We&#8217;ve heavily invested in the [Juniper SRX](http://www.juniper.net/us/en/products-services/security/srx-series/).

The SRX mostly does what we ask of it (talk to me about Oracle replication through one and their SQL ALG).

The SRX has some limitation as far as management and display of eye candy.

While I personally like a CLI to rummage around in, not everyone does.  [Palo Alto Networks](http://www.paloaltonetworks.com) has an amazing GUI.  Like, the best I&#8217;ve ever seen.  Sonicwall&#8230;&#8230;well, theirs always left me wanting back in the day.  Now&#8230;..wow, a totally different ballgame.

Don&#8217;t get me wrong, I&#8217;m not confident that the Sonicwall &#8220;Super Massive&#8221; won&#8217;t compete (in this guys opinion) with a Juniper 5800.  **However, **their transparent mode is a tad better and their web management is an order of magnitude better.  Performance?  I don&#8217;t think anything can touch an SRX loaded with SPCs, but the numbers are impressive.  I&#8217;d like to do a bake off once I get some time (and a super massive in my lab)

That being said, I gave the Sonicwall we have as a demo a good go around.  I found it&#8217;s ease of setup pretty refreshing.  For those that have non-networking savvy security folks running these boxes, they&#8217;ll likely love the interface.  I like the AppFlow Monitor.  It&#8217;s a nice reprensentation of the transit data in an easy to understand format.  Here is an example of the box in my lab after running a few days.

[<img class="alignnone  wp-image-116" title="SonicWall AppFlow Monitor " src="http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.09.41-PM-1024x256.png" alt="" width="491" height="123" srcset="http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.09.41-PM-1024x256.png 1024w, http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.09.41-PM-300x75.png 300w, http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.09.41-PM-550x137.png 550w, http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.09.41-PM.png 1176w" sizes="(max-width: 491px) 100vw, 491px" />](http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.09.41-PM.png) [  
](http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.09.41-PM.png) 

&nbsp;

The threat reports are nice as well, very eye candy and they seem pretty accurate based on what we threw at it and what we generally see in the wild west.

&nbsp;

[<img class="wp-image-120 alignleft" title="Screen Shot 2012-12-07 at 4.09.48 PM" src="http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.09.48-PM-1024x256.png" alt="" width="491" height="123" srcset="http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.09.48-PM-1024x256.png 1024w, http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.09.48-PM-300x75.png 300w, http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.09.48-PM-550x137.png 550w, http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.09.48-PM.png 1178w" sizes="(max-width: 491px) 100vw, 491px" />](http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.09.48-PM.png)

[<img class="wp-image-123 alignleft" title="Screen Shot 2012-12-07 at 4.09.41 PM" src="http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.09.41-PM1-1024x256.png" alt="" width="491" height="123" srcset="http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.09.41-PM1-1024x256.png 1024w, http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.09.41-PM1-300x75.png 300w, http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.09.41-PM1-550x137.png 550w, http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.09.41-PM1.png 1176w" sizes="(max-width: 491px) 100vw, 491px" />](http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.09.41-PM1.png)

[<img class="wp-image-121 alignleft" title="Screen Shot 2012-12-07 at 4.10.00 PM" src="http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.10.00-PM-1024x256.png" alt="" width="491" height="123" srcset="http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.10.00-PM-1024x256.png 1024w, http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.10.00-PM-300x75.png 300w, http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.10.00-PM-550x137.png 550w, http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.10.00-PM.png 1173w" sizes="(max-width: 491px) 100vw, 491px" />](http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.10.00-PM.png)

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

The real time monitor reminds me a lot of the Palo Alto.  It gives some serious eye candy, live, realtime graphs of any traffic transiting the box.  Very eye catching and I can see a use case for it.

[<img class="alignnone  wp-image-130" title="Sonicwall Real Time Monitor" src="http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.48.44-PM-1024x635.png" alt="" width="524" height="325" srcset="http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.48.44-PM-1024x635.png 1024w, http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.48.44-PM-300x186.png 300w, http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.48.44-PM-550x341.png 550w, http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.48.44-PM.png 1215w" sizes="(max-width: 524px) 100vw, 524px" />](http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.48.44-PM.png)

However, I find the management of the interfaces a bit clunky and the lack of non-beta IPv6 support is a but disappointing.  I&#8217;ll be testing the IPv6 support soon, I&#8217;m just waiting on the activation of the box I have to support it.

Firmware updates seem to require a registration of the machine in their system, something I understand but the old school networking guy in me really hates feature licensing and remote activation of network hardware.  A lot.  the fact that every vendor seems to be doing it just makes my skin crawl, but such is life.

The box comes with an SSL VPN server as well, I&#8217;ve still been twiddling with getting mine working.  The smaller SOHO devices have wifi built in, but that&#8217;s way outside of my scope, so I&#8217;ll leave it at that.

&nbsp;

The CLI isn&#8217;t terrible, either.  It&#8217;s more IOS that I remember, but a far cry from JunOS.  Tab complete works and there are a decent amount of options.  I&#8217;ve not yet tried to configure much with it but have used the show commands some.  Here is an example from the small box we have:

&nbsp;  
,,,,,,,,,,,,,,,  
,,,mmbbbbbb11111111111111111111111bbbbbmm,,,  
,,,b||PPPPPPP||&#8220;&#8220;&#8220;&#8220;&#8220;&#8220;&#8220;&#8220;|PPPPPPPPP111111111111bbm,,  
&#8220;&#8220;&#8220; &#8220;&#8220;\`PPPP111111111bm,  
&#8220;\`PP1111111bm,  
\`PP111111b,  
|111111:  
.1111P|.  
Copyright (c) 2010 SonicWALL, Inc.                                                                                  ,b1PP|\`  
,,||&#8220;\`  
User:admin  
Password:

labfw> show interface sta  
labfw> show interface statistics  
Interface statistics for X0  
InDiscards : 0  
InNUcast : 401464  
InUcast : 4921467  
InOctets : 2207976060  
InErrs : 0  
OutDiscards : 37  
OutNUcast : 9733  
OutUcast : 5407031  
OutOctets : 3031626437  
OutErrs : 0  
InUnkProto : 0  
InMcast : 291793  
InBcast : 109671  
OutMcast : 0  
OutBcast : 9733

Interface statistics for X1  
InDiscards : 0  
InNUcast : 5401982  
InUcast : 4496250  
InOctets : 3192806274  
InErrs : 0  
OutDiscards : 0  
OutNUcast : 54  
OutUcast : 4582195  
OutOctets : 2114718776  
OutErrs : 0  
InUnkProto : 0  
InMcast : 1500142  
InBcast : 3901840  
OutMcast : 0  
OutBcast : 54

&nbsp;

Overall, not a bad platform.  They&#8217;ve certainly done their homework.