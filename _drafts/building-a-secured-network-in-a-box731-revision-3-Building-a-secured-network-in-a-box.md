---
id: 739
title: Building a secured network in a box
date: 2013-07-25T22:59:37-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2013/07/731-revision-3/
permalink: /2013/07/731-revision-3/
---
In many environments, the move to virtualization is a path well traveled.  My home and lab networks are no exception to this.  I have played with nearly all of the virtualization platforms and am firmly in the camp that there will be a large segment of networking that will move to a virtualized platform, especially in the data center and campus segments.  Virtualization of routing tables has existed for a long time, see <a href="http://en.wikipedia.org/wiki/Virtual_Routing_and_Forwarding" target="_blank">VRF-Lite  and MPLS VRF </a>as well as multi-tenancy technologies like Junipers logical systems.

&#8220;How is a small to medium sized environment going to take advantage of this and more interestingly, how can it be secured?&#8221;

[<img class="alignleft  wp-image-732" alt="Red_onions" src="http://www.forwardingplane.net/wp-content/uploads/2013/07/Red_onions-1024x763.jpg" width="368" height="275" srcset="http://www.forwardingplane.net/wp-content/uploads/2013/07/Red_onions-1024x763.jpg 1024w, http://www.forwardingplane.net/wp-content/uploads/2013/07/Red_onions-300x223.jpg 300w, http://www.forwardingplane.net/wp-content/uploads/2013/07/Red_onions-550x410.jpg 550w, http://www.forwardingplane.net/wp-content/uploads/2013/07/Red_onions.jpg 1600w" sizes="(max-width: 368px) 100vw, 368px" />](http://www.forwardingplane.net/wp-content/uploads/2013/07/Red_onions.jpg)This is a question I inadvertently found at least one answer to when building out my own network and testing a great little project called <a href="http://securityonion.blogspot.com/" target="_blank">security onion</a>.  Now I&#8217;d seen and used this platform a bit in the past, but it had been at least a version ago and my exposure was pretty short.

The problem now, though, was that everyting I have in use other than a gigabit switch and a NAS is virtualized.  My firewall, my router, all of my dev boxes and all but one of my non-portable machines.  All VMs.  I&#8217;d gone back and forth between VMware and KVM, and while I like KVM better, management of edge case or non-standard networking stuff wasn&#8217;t as well documented and <a href="http://openvswitch.org/" target="_blank">OVS</a> either wasn&#8217;t in the build of CentOS or I didn&#8217;t know about it yet, so I settled on VMware ESXi 5 for this particular box.

Interestingly enough, the VMWare operating system has a mechanism for &#8220;spanning&#8221; a port.  More correctly, it has a way to see &#8220;all vlans&#8221; on a given vswitch, and it&#8217;s quite simple.  Essentially, you have to create a port group on vlan 4095 on the vswitch then set that port group to promiscuous mode. Add the vm NIC that you are going to use to monitor traffic to that port group.  <a href="http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1004099" target="_blank">From VMware site</a>:

<p style="text-align: center;">
  <a href="http://www.forwardingplane.net/wp-content/uploads/2013/07/VMWare-site.png"><img class="size-full wp-image-734 aligncenter" alt="VMWare-site" src="http://www.forwardingplane.net/wp-content/uploads/2013/07/VMWare-site.png" width="728" height="264" srcset="http://www.forwardingplane.net/wp-content/uploads/2013/07/VMWare-site.png 728w, http://www.forwardingplane.net/wp-content/uploads/2013/07/VMWare-site-300x108.png 300w, http://www.forwardingplane.net/wp-content/uploads/2013/07/VMWare-site-550x199.png 550w" sizes="(max-width: 728px) 100vw, 728px" /></a>
</p>

 [<img class="wp-image-735 alignright" alt="VMWAre-config-networking" src="http://www.forwardingplane.net/wp-content/uploads/2013/07/VMWAre-config-networking.png" width="564" height="350" srcset="http://www.forwardingplane.net/wp-content/uploads/2013/07/VMWAre-config-networking.png 783w, http://www.forwardingplane.net/wp-content/uploads/2013/07/VMWAre-config-networking-300x186.png 300w, http://www.forwardingplane.net/wp-content/uploads/2013/07/VMWAre-config-networking-550x341.png 550w" sizes="(max-width: 564px) 100vw, 564px" />](http://www.forwardingplane.net/wp-content/uploads/2013/07/VMWAre-config-networking.png)This is where you tell security onion to have interfaces on both of the vswitches. Here are a few screenshots of my VMware config following the steps laid out above. It&#8217;s far more simple than I could have imagined.

&nbsp;

&nbsp;

Configuration, Networking, Properties, Security. VLAN 4095.

[<img class="alignleft  wp-image-736" alt="VMWare-SPAN-WAN1" src="http://www.forwardingplane.net/wp-content/uploads/2013/07/VMWare-SPAN-WAN1.png" width="452" height="332" srcset="http://www.forwardingplane.net/wp-content/uploads/2013/07/VMWare-SPAN-WAN1.png 754w, http://www.forwardingplane.net/wp-content/uploads/2013/07/VMWare-SPAN-WAN1-300x220.png 300w, http://www.forwardingplane.net/wp-content/uploads/2013/07/VMWare-SPAN-WAN1-550x403.png 550w" sizes="(max-width: 452px) 100vw, 452px" />](http://www.forwardingplane.net/wp-content/uploads/2013/07/VMWare-SPAN-WAN1.png)

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

[<img class=" wp-image-737 alignright" alt="VMWARE-Span-WAN2" src="http://www.forwardingplane.net/wp-content/uploads/2013/07/VMWARE-Span-WAN2.png" width="300" height="373" />](http://www.forwardingplane.net/wp-content/uploads/2013/07/VMWARE-Span-WAN2.png)

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

At this point Security onion should be able to see what is going on.  In my case I allowed for visibility on both sides of my routing firewall.  This is the interesting part, I think.  My initial thoughts are that this could be a &#8220;network in a box&#8221; for small offices.  No router, no servers (other than the VMware host), essentially a fully functional &#8220;enterprise&#8221; network of hosts, including a very high quality IDS device in a single device.  Put whatever firewall / vrouter in there you want, <a href="http://www.pfsense.org" target="_blank">pfsense</a>, <a href="http://www.juniper.net" target="_blank">Juniper vSRX</a>, <a href="http://www.fortinet.com" target="_blank">fortinet</a>, <a href="http://www.paloaltonetworks.com" target="_blank">Palo Alto</a>, they all have virtual devices and they all do a fine job [with the exception of IPv6; the only one I could get DHCPv6-PD to work with was pfsense].  Still need to test the fortinet.

Is this a viable option?  I have no idea, but it does work well.  In fact, ironically enough, the day I got this working (July 13, 2013), a post went up over at <a href="http://www.geekempire.com/2013/07/virtual-security-onion-via-ubuntu-kvm.html" target="_blank">GeekEmpire</a> doing almost exactly the same thing with KVM and OVS.  The setup is shockingly similar, right down to using pfSense. I was actually a bit envious, not only because his post went up first, but because he did what I had actually wanted to do by using KVM and OVS.  It&#8217;s well done, I recommend reading it.