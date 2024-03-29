---
id: 219
title: 'A tale of two ISPs&#8230;'
date: 2012-10-18T05:24:00-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2012/10/20-revision/
permalink: /2012/10/20-revision/
---
     I&#8217;ve been doing research, carrier and service provider networking for a long time.  I my first real service provider experience was beta testing DSL for GTE back in the 1990s, I prototyped and proposed a CLEC for an employer in 1998 and went to work for the only ISP in the area rolling it&#8217;s own DSL over ATM in early 2000.  
    Everything seems to come full circle, though, given enough time.  Right now I&#8217;m working on many projects, but two of them jumped out as particularly interesting when contrasted against each other.  Alone they&#8217;re interesting but not anything never done before.  When compared, however, they become are polar opposites in case studies.  
    The first, a smaller mom-and-pop ISP that is now pretty much a WISP for only rural customers, was originally part of the ISP I rebuilt back in 2000.  They had not employed a network engineer after I left in 2002, but retained a good tech who had great skill with RF but not enough time to really learn the ins and outs of routing.  
The infrastructure was mostly stagnant for about 10 years, adding a new switch or a box to do some traffic shaping, but it was, in essence, a very large layer 2 network with one router at the border.  
    The other ISP is a bleeding edge winner of the broadband project of the year award, heavily funded and very innovative in nature, offering 1GBps fiber to the home and unlimited access to all local resources that want to connect.    
    I was the senior network engineer for the ISP 10 years ago and was appointed lead network engineer for the fiber ISP project.  It&#8217;s interesting that both came to my circle of view at the same time, as I work on the fiber ISP in my &#8220;day job&#8221; and rebuild the WISP at night in my spare time as a consultant. 

A few take aways that I&#8217;ve [re-]discovered are:

A pfsense box makes a fantastic router for a smaller operation.  It also makes a completely acceptable replacement for a Cisco for far less money.  
Even spending half a million dollars with Cisco does **<u>not</u>** entitle you to any features that may be available in the SUP2T hardware (and not yet in the software).  Lame, cisco, lame.  
HP procurve makes very nice Layer2 boxes with lifetime warranties.  
Cutting over an ISP live really is not a lot of fun.  
Not having PI address space is **very** inconvenient.  
Traffic shaping, rate limiting or QoS are possibly my least favorite thing to do now.  
End users don&#8217;t care about IPv6 (boo! hiss!)

More to come, including:

How the Cisco Sup2T doesn&#8217;t actually have software support for microflow policing yet  
How to provision IPv6 RA through an Adtran TA5000  
How to alias an overlay network on pfSense

I guess I can sleep when I&#8217;m dead =)

<div>
  [[ This is a content summary only. Visit my website for full links, other content, and more! ]]
</div>