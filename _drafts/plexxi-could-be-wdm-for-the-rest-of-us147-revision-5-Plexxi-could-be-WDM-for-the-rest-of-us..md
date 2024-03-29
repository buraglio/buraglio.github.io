---
id: 167
title: Plexxi could be WDM for the rest of us.
date: 2012-12-10T23:02:14-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2012/12/147-revision-5/
permalink: /2012/12/147-revision-5/
---
[Plexxi](http://www.plexxi.com) is an interesting product that has recently emerged in the data center space.  While data center, fabric and cloud are all the rage in the buzzword world of data networking, this one caught my attention because it was something unique that I&#8217;d not seen before.  Their TOR boxes have a few interesting additions to them, the first of which is a WDM port on the back. Now, I&#8217;m not a stranger to the WDM world.  I&#8217;ve been helping maintain a DWDM network for a little over a decade, but seeing this, by default, in a data center positioned switch?  Now that got my attention.

For those that don&#8217;t know what that is, it&#8217;s the ability to slice up spectrum of light into what telco (and other networking folks) call waves. Each wave is a different &#8220;color&#8221; or wavelength.  They call this &#8220;Affinity Networking&#8221; and it allows for the ability to provision more bandwidth over a single pair of fiber.  For example, say you have a pair of fiber from one data center to another, either in the same facility or across your city (distances up to 10K now, 70K on the roadmap).  You&#8217;d normally plug in a 1G or 10G (or 100G if you&#8217;re really, really well funded) and provision service over that pair of fiber.  You&#8217;re stuck with that interface speed, right?  Wrong. Enter WDM.   On a WDM systems you have the ability to provision, channels, sometimes in huge amounts, over the same pair.  I&#8217;ve seen multiple 100G waves, OC192 Waves, a plethora of 10G waves and a few 1G waves all working fine over the same pair of fiber.

[<img class="aligncenter size-full wp-image-163" title="prism4c" src="http://www.forwardingplane.net/wp-content/uploads/2012/12/prism4c.gif" alt="" width="400" height="300" srcset="http://www.forwardingplane.net/wp-content/uploads/2012/12/prism4c.gif 400w, http://www.forwardingplane.net/wp-content/uploads/2012/12/prism4c-300x225.gif 300w" sizes="(max-width: 400px) 100vw, 400px" />](http://www.forwardingplane.net/wp-content/uploads/2012/12/prism4c.gif)

Plexxi &#8220;Affinity Networking&#8221; boasts the ability to do WDM right in the back of their 32 port 10G switches.

Very slick.  But that&#8217;s not the coolest part.  Enter part 2.  They also boast Software Defined control over the product, enabling dynamic provisioning of  bandwidth, on demand..

Now, I have not yet hand my hands on a few of these boxes, but I think that they will be a piece in what has become a changing landscape of data centers.  WDM has been around forever in the service provider wide area, but the ability to change bandwidth allocations using WDM on the fly is game changing, albeit not really new.  There have been several research projects in the past that have attempted to do this, the [DRAGON project](http://dragon.maxgigapop.net/twiki/bin/view/DRAGON/WebHome), of which one of the sites I helped maintain was a member attempted to do something like this using [GMPLS](http://en.wikipedia.org/wiki/Generalized_Multi-Protocol_Label_Switching).  Doing it in the data center?  That&#8217;s new.

From the looks of it they will be doing a proprietary SDN called &#8220;Plexxi Control&#8221; that ties all of their switches together, allowing for a flattening of the network.  I find this approach intriguing, I&#8217;m a fan of the fabric approach to layer 2 a la Juniper Qfabric or Brocade VDX, but the WDM port and the decoupled control together is unique &#8230;.and enthralling.  I look forward to seeing some of these boxes function up close and personal.  I&#8217;m especially interested in the longer distance pieces of these for remote data centers and DR locations.

For a comprehensive write up, see [this article](http://searchnetworking.techtarget.com/news/2240173858/Plexxi-SDN-includes-tiered-controller-data-center-based-WDM) by [Shamus McGillicuddy](http://searchnetworking.techtarget.com/contributor/Shamus-McGillicuddy).  [ ](http://searchnetworking.techtarget.com/news/2240173858/Plexxi-SDN-includes-tiered-controller-data-center-based-WDM)

###