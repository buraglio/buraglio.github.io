---
id: 701
title: 'I want to love cumulus networks&#8230;..'
date: 2013-07-02T15:49:54-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2013/07/678-revision-2/
permalink: /2013/07/678-revision-2/
---
I want to preface this by saying that I have not seen or worked on the cumulus networks system yet.  This is a stream of consciousness diatribe on my thoughts and opinions based on what I&#8217;ve read publicly.

Recently a <a href="http://cumulusnetworks.com/" target="_blank">new network player</a> has emerged on the scene with a very simple, straightforward idea.  Take linux and put it on a switch. While this isn&#8217;t exactly new (see Juniper and FreeBSD, Arista with Linux, Force10 with NetBSD or the plethora of other vendors using an opensource OS as the underpinnings of their NOS), the angle that cumulus networks is taking is a bit more&#8230;.raw.

Take a standard Cisco or Juniper box.  The engineers that work on these devices know a pseudo-programming language.  They program the routers using that language and syntax.  They&#8217;re familiar with it and it is well documented.  Heck, aside from JunOS and the Alcatel-Lucent, 90% of the NOS you see on equipment is arguably derivative of Cisco&#8217;s venerable IOS.  Automation is [unfortunately] not nearly as common as it could be on network gear.  Sure, there are a handful of opensource tools, overpriced, bloated and [arguably] poorly functioning tools available to &#8220;automate&#8221; and &#8220;manage&#8221; equipment, but none are that great, especially if you have a large, diverse environment.

Enter the sysadmin.  Sysadmins have been automating tasks for as long as I&#8217;ve been around.  <a href="http://cfengine.com/" target="_blank">cfengine</a>, home grown tools and now <a href="https://puppetlabs.com/" target="_blank">puppet</a> and the like are marvelous tools that are a makeshift &#8220;controller&#8221; for managing distributed systems.  Big Iron cluster admins have had tools like this forever as well.  How often are these people the same?  In a large environment where there is a need for automation I will wager that the answer to that question is &#8220;not very often&#8221;.

This is my problem with cumulus networks.  Make no mistake, I love the simplicity and idea behind it.  I think that it&#8217;s wonderfully simple and innovative.  It&#8217;s the &#8220;duh&#8221; of networking OS choices, but it introduces a lot of issues, many of which aren&#8217;t really pleasant to solve (and only a handful are actually technical).  You&#8217;ve got the fractured nature of IT in large environments.  Server guys aren&#8217;t often the same as networks guys.  Often they are in totally different silos.  This is problematic due to territoriality not to mention subject matter expertise.  Am I as a network engineer of 15+ years comfortable running *IX systems?  Sure.  Is everyone?  Likely not and even less likely on a large scale like this.

Automation is key, but even running puppet systems isn&#8217;t exactly a network engineers core competency.  I think that building those systems will be either cost prohibitive (either time or salary) or will just be a non-started because it&#8217;s &#8220;too different&#8221;.  Let me reiterate that I think it&#8217;s a very cool idea and know that it&#8217;d probably take a week or so to make work for any decent sysadmin or system savvy network engineer, but the large swath is going to recoil.

They have a quagga instance their version which provides a &#8220;non-model CLI&#8221;, and if the quagga is anything like what I&#8217;ve used it can sorta be used to manage the network, but is a poor overlay to the system tools that adds very basic routing protocols. It&#8217;s encouraging, but feels like a bolt on at face value.

Then there is the issue of the raw OS.  It&#8217;s just linux.  This statement alone opens up a new vector.  Does one need to now worry about having compromised switches?  Can my switch be turned into a bit cannon or a warez distribution site?  A Tor relay?  Hardening a switch or router like a host