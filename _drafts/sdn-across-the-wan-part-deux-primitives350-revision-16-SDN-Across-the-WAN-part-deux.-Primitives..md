---
id: 369
title: 'SDN Across the WAN, part deux.  Primitives.'
date: 2013-01-10T21:15:38-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2013/01/350-revision-16/
permalink: /2013/01/350-revision-16/
---
I&#8217;ve been <a title="SDN across domains in the WAN – a novice look" href="http://www.forwardingplane.net/2012/11/sdn-across-domains-in-the-wan-a-novice-look/" target="_blank">lamenting about the SDN WAN</a> options for a while now.  Having SDN/OpenFlow in a data center or campus is relatively well documented and already widely deployed.  Google has been doing SDM across their private WAN in production.  These pieces are easy.  What isn&#8217;t easy is the ability to plumb SDN, at a lowest common denominator, across many domains that are under disparate control.   This part is hard. What is lacking is a fundamental framework, or set of primitives to build from.  As an example, how does one build a SDN path across this:

&nbsp;

[<img class="aligncenter size-full wp-image-351" title="SDN Reference Architecture -Sanitized" src="http://www.forwardingplane.net/wp-content/uploads/2013/01/SDN-Reference-Architecture-Sanitized.png" alt="" width="470" height="704" srcset="http://www.forwardingplane.net/wp-content/uploads/2013/01/SDN-Reference-Architecture-Sanitized.png 470w, http://www.forwardingplane.net/wp-content/uploads/2013/01/SDN-Reference-Architecture-Sanitized-200x300.png 200w" sizes="(max-width: 470px) 100vw, 470px" />](http://www.forwardingplane.net/wp-content/uploads/2013/01/SDN-Reference-Architecture-Sanitized.png)

First I think we need to define what we want out of the SDN path.  A reserved bandwidth allocation?  A Layer2 path?  Flow instantiation across the entire path?  The first two have a least common denominator.  The third is hard, especially if the path transits a segment with no SDN capability.

This piece is making my brain hurt.  There seems to be a lot of early work on this, [Inder Monga](http://events.internet2.edu/speakers/speakers.php?go=people&id=2865) from [ESnet](http://www.es.net) has been working at making this happen, and I think he&#8217;s the closest from what I&#8217;ve seen in my searching and researching.   I want to know how to do this across **all** networks.   I want to see the future of carrier WAN connectivity, to taste the unicorn milk.

The methodology so far has been to break this down into small black boxes.  After doing that, I realized that there is going to have to be a common protocol.  The least common denominator to all of this is the SDN.  It doesn&#8217;t much matter what that SDN is as long as there is a central controller.  It can be OpenFlow, <a href="http://www.es.net/services/virtual-circuits-oscars/" target="_blank">OSCARS</a>, <a href="http://en.wikipedia.org/wiki/Generalized_Multi-Protocol_Label_Switching" target="_blank">GMPLS</a>, <a href="http://ext.delaat.net/olex/index.html" target="_blank">Open LightPath Exchange</a>, whatever.  It doesn&#8217;t matter.  They all need a controller.  Within those controllers there needs to be &#8220;an energy field created by all SDN. It surrounds us and penetrates us; it binds the galaxy together&#8221;.  Yes, I like Star Wars.

So, how would one do this?  It would be ideal, to me at least, if there was a standard set of protocols that all of these controllers could speak.  This standard communication could be as simple as how a BGP peering functions.  Site A has a controller, it &#8220;peers&#8221; with it&#8217;s upstream and announces its capabilities.

For example,  
[<img class="aligncenter size-full wp-image-352" title="SDN peering" src="http://www.forwardingplane.net/wp-content/uploads/2013/01/SDN-peering.png" alt="" width="591" height="740" srcset="http://www.forwardingplane.net/wp-content/uploads/2013/01/SDN-peering.png 591w, http://www.forwardingplane.net/wp-content/uploads/2013/01/SDN-peering-239x300.png 239w, http://www.forwardingplane.net/wp-content/uploads/2013/01/SDN-peering-550x688.png 550w" sizes="(max-width: 591px) 100vw, 591px" />](http://www.forwardingplane.net/wp-content/uploads/2013/01/SDN-peering.png)

All of these peers exchange capability information and pass it on with a standardized set of language and a location identifier (think ASN and route announcements).  To me this appears to be the lowest hanging fruit. I&#8217;m not a developer but there doesn&#8217;t seem to be to be any reason that this couldn&#8217;t be built into any controller, commercial or opensource. That way, regardless of vendor, SDN implementation or capabilities everyone can create a SDN path based on the available implementations upstream. Of course, there would need to be a &#8220;multihop&#8221; option for those that have to upstream SDN paths. In this case something like a GRE tunnel could be the lowest common denominator. This would have to transcend OpenFlow and be a true &#8220;SDN&#8221; at the fundamental level to actually work, but it needs to take into account managing the flow table of networks outside of a given administrative domain. As a starting point, here is the framework I came up with:

  * Reliable transport: TCP
  * Authentication method: MD5 Capabilities exchanged:
  * Number of circuits
  * Types of SDN (MPLS, VLAN, DWDM Waves, OpenFlow Version, Flow manipulation)
  * Bandwidth per circuit (if applicable)
  * Duration of circuit or flow (path TTL, permanent?)
  * Path validation (to ensure end to end connectivity over negotiated methodology)

I&#8217;ve been talking a lot with <a href="http://www.networkstatic.net/" target="_blank">Brent Salisbury</a> about this.  I know folks are thinking about it.  Bill Owens [had some great comments](http://www.forwardingplane.net/2012/11/sdn-across-domains-in-the-wan-a-novice-look/#comment-47) to my last post regarding this and I think he&#8217;s totally spot on.  However, I want to hit 88mph in my Delorean and see the future.  I think it&#8217;s a ways way off but someone needs to come up with this framework.  SDN is so disjointed that it needs a one ring.  Controlling the forwarding plane of someone else network is scary and needs to have a leash on it.  Building this standard protocol could be it.  Unfortunately, I am no developer but I do know a little bit about running a decent sized network.  There will need to be safeguards, policy and knobs to tweak.  I keep coming back to BGP.  It&#8217;s not as much of a routing protocol as it is a policy framework disguised as a routing protocol.  There needs to be something similar with SDN.

I&#8217;m going to continue to think through this publicly and I welcome constructive input.

<pre></pre>