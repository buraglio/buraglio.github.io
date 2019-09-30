---
id: 593
title: 'OpenFlow Hybrid.  It&#8217;s a must, not an option.'
date: 2013-04-15T14:41:04-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2013/04/572-revision-4/
permalink: /2013/04/572-revision-4/
---
OpenFlow is, of course, a hot buzzword.  It&#8217;s the newest, and in my opinion, the most innovative thing to hit data networking since dynamic routing.  The ability to programmatically, systematically and potentially dynamically control traffic at the flow level through a network is innovative, exciting and terrifying [to many network engineers and architects] at the same time.  Allowing applications to touch the network change behavior is something that many engineers are not terribly comfortable with.  I will even admit that a few years ago I was pretty tentative about software changing network hardware.  <a title="Black Hole routing" href="http://www.forwardingplane.net/2011/10/black-hole-routing/" target="_blank">Building a Blackhole router</a> was an easy way for me to acquaint myself with this and get comfortable with software changing things without human interaction.   Most of my discomfort with this process was the fact that I&#8217;m not a good developer.  I can hack scripts and read most basic code in Shell, C, Perl, Python and Ruby but I don&#8217;t actively do anything but an occasional script or <a title="VDXrancid contrib scripts" href="http://www.forwardingplane.net/2012/11/vdxrancid-contrib-scripts/" target="_blank">hack</a> <a title="alurancid and pfrancid" href="http://www.forwardingplane.net/2011/06/alurancid-and-pfrancid/" target="_blank">to</a> <a title="Alcatel Lucent RANCID scripts" href="http://www.forwardingplane.net/2010/12/alcatel-lucent-rancid-scripts/" target="_blank">existing projects</a>.

[<img class="size-medium wp-image-592 alignright" alt="Enterprise Network" src="http://www.forwardingplane.net/wp-content/uploads/2013/04/Enterprise-Network-265x300.jpg" width="265" height="300" srcset="http://www.forwardingplane.net/wp-content/uploads/2013/04/Enterprise-Network-265x300.jpg 265w, http://www.forwardingplane.net/wp-content/uploads/2013/04/Enterprise-Network-550x621.jpg 550w, http://www.forwardingplane.net/wp-content/uploads/2013/04/Enterprise-Network.jpg 606w" sizes="(max-width: 265px) 100vw, 265px" />](http://www.forwardingplane.net/wp-content/uploads/2013/04/Enterprise-Network.jpg)Conversely, we&#8217;re all pretty comfortable with networks as they exist today.  The typical &#8220;enterprise pyramid&#8221; is best practice and works very well.  Good physical design is good physical design.  However, where this, and any other network gets hairy is when it scales to hyper scale or the operations team is

&nbsp;

&nbsp;

&nbsp;

&nbsp;

The OFP\_Normal configuration will send the packet in the OF pipeline to the native switching pipeline for packet forwarding. OFP\_Normal is only used as a default forwarding mechanism in this case, very much like default routes in routing.  OF_Normal at the bottom,

SDN gateways have a much more traditional look and feel. They have a flat SDN OpenFlow network with a default gateway for client traffic by either controller proxy or direct reachability by the client host. Note that both approaches suffer from lack of adoption and maturity, which adds risk to any early production SDN.  IPv6-like