---
id: 1049
title: Aging hardware, IPv6 and the growing route table
date: 2014-08-12T23:05:24-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2014/08/1043-revision-v1/
permalink: /2014/08/1043-revision-v1/
---
I&#8217;ve <a title="BGP tools; troubleshooting and monitoring external routing in a nutshell" href="http://www.forwardingplane.net/2014/03/bgp-tools-troubleshooting-and-monitoring-external-routing-in-a-nutshell/" target="_blank">blathered on about BGP</a> <a title="Tuning BGP installed IPv6 routes" href="http://www.forwardingplane.net/2013/03/tuning-bgp-installed-ipv6-routes/" target="_blank">forever</a>.  Say what you will about the venerable protocol, it runs the interwebs, is reliable, extendable and well documented.  I&#8217;ve also <a title="My SDN soapbox (now with IPv6!)" href="http://www.forwardingplane.net/2013/03/my-sdn-soapbox-now-with-ipv6/" target="_blank">espoused</a> <a title="Joint Techs Summer 2011 IPv6 talks" href="http://www.forwardingplane.net/2011/07/joint-techs-summer-2011-ipv6-talks/" target="_blank">ad nauseam</a> <a title="IPv6 Features matrix for Network Hardware" href="http://www.forwardingplane.net/2011/03/ipv6-features-matrix-for-network-hardware/" target="_blank">about</a> <a title="And a purple pony." href="http://www.forwardingplane.net/2012/11/and-a-purple-pony/" target="_blank">IPv6</a>, so none of this [admitted] rant should really be a surprise coming from me.

As of 8/12/2014, according to the <a href="http://www.cidr-report.org/as2.0/#General_Status" target="_blank">CIRD report</a> (and many mailing lists), the <a href="http://en.wikipedia.org/wiki/Default-free_zone" target="_blank">default free</a> global ipv4 routing table has reached 512k routes.  This is a milestone from many perspectives, but more importantly, it solidifies the fact that there is a great deal of equipment in critical points in the internet that is out of date and cannot perform as intended in its current configuration or function.

[<img class="aligncenter wp-image-1045" src="http://www.forwardingplane.net/wp-content/uploads/2014/08/8-12-2014-plot.png" alt="8-12-2014-plot" width="566" height="428" />](http://www.forwardingplane.net/wp-content/uploads/2014/08/8-12-2014-plot.png)

This is a problem.  This is a problem for old hardware.  This is a problem for anyone that says their border router is &#8220;good enough&#8221;, and expects to take a default free table.  It&#8217;s a problem for anyone that wants to be multihomed on sub-par hardware.  I don&#8217;t think that many engineers would be surprised at how common this really is because network hardware is expensive, especially appropriate hardware that runs at site borders and in internet backbones, and by nature network engineer want to &#8220;make things work&#8221;.  I assert, however, that this may not be the best idea.

The increased size of the default free zone has been forecasted for **_years,_**_ _and with the inclusion of the 16k of ipv6 prefixes (<a title="The sad state of IPv6 and why you need to learn it." href="http://www.forwardingplane.net/2013/08/the-sad-state-of-ipv6-and-why-you-need-to-learn-it/" target="_blank">you are running IPv6</a>, **_right_**?), resources quickly become exhausted on aging hardware.  This causes a cascading problem.  Forget the odd issues seen by not having enough TCAM to house the entire default free ipv4 table.  That problem is a haymaker swing that was telegraphed **_long_** ago and should have been coming; that ship has sailed.

The bigger problem is that in flurrying around to deal with smaller TCAM sizes on gear that should have been replaced years ago, one course of action is to  repartition the TCAM, stripping away space allocated for IPv6 and allocating it to IPv4 in order to remain &#8220;default free&#8221; v4 tables.  I know because I&#8217;ve had to do this.  And it sucked. Personally, I felt a little like a sell out since I was robbing Peter to pay Paul and keep our &#8220;beloved&#8221; IPv4 running at the expense of the protocol we should have been migrated to years before but could not due to fear, uncertainty, doubt and, frankly, sheer laziness on the part of executives, developers, vendors and engineers. Blech.  I don not even like typing that.  We, I promise you,  in come cases are prolonging the deployment of IPv6 in favor of keeping v4 working due to this limitation.  And it stinks.  Like a skunk. Dipped in sewage. Wrapped in garbage.  Blown through an onion.

It&#8217;s a banner day, make no mistake.  512k ipv4 routes in the global default free ipv4 table is a milestone.  However, lets not forget that much of the pain involved in expanding the ability to use more v4 would probably have been better served in expanding ipv6 support.  Be a catalyst for change and start learning and evangelizing IPv6.

I often have a thought when discussing the merits of ipv6 with anyone that is arguing as to why they don&#8217;t want or need to deploy it:

Would the internet/their network be a better place if we spent as much time making ipv6 work instead of going well out of our way to work around it?

<end rant> =)

&nbsp;

&nbsp;