---
id: 150
title: 'Brocade VDX First Impressions&#8230;.'
date: 2012-12-08T12:04:40-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2012/12/8-revision-2/
permalink: /2012/12/8-revision-2/
---
I recently had the opportinity to work with the much-anticipated [Brocade VDX &#8220;Ethernet Fabric&#8221;](http://www.brocade.com/launch/cloud-clarity/solutions-technology-innovation.html) platform.  I do admit tha tI&#8217;m intrigued by this product.  I&#8217;d seen it work multiple times in demos and it worked so well and looked to easy that we actively tried to throw curve balls at the demo organizer to prove it wasn&#8217;t canned.

<img class="aligncenter" src="http://www.brocade.com/images/products/vdx-6720-dc-switches/VDX6720-24_front_large.jpg" alt="" width="375" height="240" /> 

It succeeded.

The hardware hashing across the VLAGs is very slick.  The VMware VSwitch integration worked well and was handy.  With the movement to virtualization, this is an important piece for most data center folks.

That being said, some people have very specific data center requirements that aren&#8217;t really the same as an enterprise.  For example:

  * Don&#8217;t firewall everything at the DC. That&#8217;s right. I said it.  Firewalls don&#8217;t solve all security problems.  Take that &#8220;defense in depth&#8221;!
  * A potential need to do non-standard or experimental protocols.
  * A lot of line rate 10G internally and to the rest of network.
  * Integration with legacy, existing and or in-house written tools
  * Need for GSLB/SLB
  * Self Healing
  * Ease of fabric upgrade (software upgrade doesn&#8217;t cause fabric isolation)
  * Ease of fabric upgrade (increase LAG numbers and capacity easily)
  * Multi-Homed hosts
  * IPv4
  * IPv6
  * IPv4 Multicast
  * Future SDN support
  * NAT
  * Public Address space
  * All at the same time

[<img class="alignnone size-full wp-image-149" title="Flexible DC" src="http://www.forwardingplane.net/wp-content/uploads/2012/11/Flexible-DC.jpg" alt="" width="635" height="720" srcset="http://www.forwardingplane.net/wp-content/uploads/2012/11/Flexible-DC.jpg 635w, http://www.forwardingplane.net/wp-content/uploads/2012/11/Flexible-DC-264x300.jpg 264w, http://www.forwardingplane.net/wp-content/uploads/2012/11/Flexible-DC-550x623.jpg 550w" sizes="(max-width: 635px) 100vw, 635px" />](http://www.forwardingplane.net/wp-content/uploads/2012/11/Flexible-DC.jpg)

&nbsp;

The Brocade VDX does most of this.  The unexpected things I ran into with my very brief hands-on with the VDX were just that, unexpected.  I could reliably crash ssh on the boxes by sending a public key at login, which is default behavior for a normal ssh client.  This was very annoying and implied that they don&#8217;t yet support ssh keys for authentication.  One can work around it by doing _ssh -o PubkeyAuthentication=no -l <name>_ and worked with the newest version of putty, which I don&#8217;t use.  The version of OpenSSH on my Mac running 10.8.2 had an issue with it, as did the linux jumphost I used.

There is no way, in current software to manage this centrally like you can with qfabric.  Each device is an individual switch.  I suspect this will change since it&#8217;s pretty inconvenient and I know many folks have asked for it.  This was my biggest issue with it.

It doesn&#8217;t run spanning tree.  It has a loop detection mechanism, but it isn&#8217;t spanning tree.  It&#8217;s not meant to have anything but end hosts or other VDX plugged into it from what I gather, other than uplinks.

It is easily integrated into RANCID. [I hacked together a script to do this](http://www.forwardingplane.net/2012/11/vdxrancid-contrib-scripts/) in about 10 minutes and I&#8217;m an awful programmer.

It looks EXACTLY like IOS so folks familiar with Ciscos venerable IOS command line will have absolutely no issue picking this right up.

Bear in mind that this is a relatively new product.  I would probably place the best competitor for this as the Juniper Qfabric or Microfabric, bith of which are a larger scale product and suffer from some of the same issues.  I&#8217;m excited to see more about it, it did its job pretty well.  Juniper take no