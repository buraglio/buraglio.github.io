---
id: 62
title: 'SDN across domains in the WAN &#8211; a novice look'
date: 2012-11-30T14:53:57-06:00
author: Nick Buraglio
layout: revision
guid: http://new.forwardingplane.net/2012/11/4-revision-2/
permalink: /2012/11/4-revision-2/
---
<span style="font-family: inherit;">There has been a flurry of discussion on SDN in the WAN lately, specifically, why and how.  Brent Salsbury laid out a few use cases <a href="http://networkstatic.net/sdn-use-cases-for-service-providers/" target="_blank">here</a>.  The why seems pretty straightforward.  I do believe it will happen, however, the <strong>how </strong>is the interesting part.  Admittedly, I&#8217;m a tad of a greenhorn in the SDN space, I&#8217;ve made it work in a lab, I participate as much as I can in the working groups and I attempt (poorly) to keep up.  </span>  
<span style="font-family: inherit;">SDN, and likely OpenFlow, is in our roadmap at work.  Doing SDN in the data center is well documented and fairly well tested. Stanford has it all over their campus LAN and Google is pushing it around their walled garden WAN on custom built hardware.  None of this is new.  </span>  
<span style="font-family: inherit;">The interesting bit is <strong>how do you do it across multiple administrative entities</strong>? </span>  
<span style="font-family: inherit;">As I said before, I&#8217;ll never claim to be an SDN expert, so I need to break this down into simple pieces for my limited mind to comprehend.  </span>  
<span style="font-family: inherit;">BGP solved this years and years ago, how is that accomplished?  Can any of these bits be re-used (why re-invent the wheel)?</span>  
<span style="font-family: inherit;"><br /> </span><span style="font-family: inherit;">My caveman mind wants to break this down into requirements:</span>  
<span style="font-family: inherit;"><br /> </span><span style="font-family: inherit;">This can likely be controlled by access between peers via an access control mechanism of some sort, i.e. place software limits on how much a given peer can provision in your network, which can be broken down into:</span>

  * <span style="font-family: inherit;">Number of circuits</span>
  * <span style="font-family: inherit;">Types of circuits (MPLS, VLAN, DWDM Waves, etc.)</span>
  * <span style="font-family: inherit;">Bandwidth per circuit</span>
  * <span style="font-family: inherit;">Duration of circuit (path TTL, permanent?)</span>
  * <span style="font-family: inherit;">Number of devices involved per circuit</span>
  * <span style="font-family: inherit;">Types of SDN (OpenFlow versions, OSCARS, etc)</span>
  * <span style="font-family: inherit;">Probably more stuff</span>

<span style="font-family: inherit;">How can this be done?  I don&#8217;t currently know enough to answer that question, but I suspect it may require a little bit of work in adding a peering framework between control planes (SDN controllers) not unlike how BGP works.  To put this in familiar terminology, for example,</span>  
<span style="font-family: inherit;"><br /> </span>

  * <span style="font-family: inherit;">Route maps could be replaced by permissions maps or even an ACL of some sort to establish the abilities of each peer.  </span>
  * <span style="font-family: inherit;">Peers would need to agree (</span><span style="font-family: inherit;">configuration-wise and politically) on what abilities can be exchanged before peers could operate, </span>programmatically<span style="font-family: inherit;"> agree on parameters before any changes can be made.</span>
  * <span style="font-family: inherit;"><span style="font-family: inherit;">Security parameters would need to be met for the peers to establish to contain the control plane traffic in a safe way, much like an MD5 across a BGP peering.</span></span>

<span style="font-family: inherit;">If this sounds like a tall order, I&#8217;ll wager you&#8217;re right and I&#8217;ll also bet that before it happens we&#8217;ll have a Blu Ray vs HD-DCD or VHS vs Beta throw down of SDN protocols.  </span>  
<span style="font-family: inherit;">Folks have been trying to do this for years, the <a href="http://dragon.maxgigapop.net/twiki/bin/view/DRAGON/WebHome" target="_blank">DRAGON project</a> tried this years ago and did a decent job.  Our Arlington, VA site was one of the original build outs of it. <a href="https://oscars.es.net/OSCARS/docs/" target="_blank">OSCARS</a> is doing similar stuff and is actively working across <a href="http://www.es.net/" target="_blank">ESnet</a>. <a href="http://www.internet2.edu/ion/" target="_blank">Internet2 ION</a> is another attempt.</span>  
<span style="font-family: inherit;">These have all had their effect on the Research and Education networks, but to be adopted acrossm and more importantly between, service provider networks, there needs to be ways to do them elegantly and securely.  There is nothing that a SP hates more than risk, and without these control mechanisms, there is a pretty large amount of risk. </span>  
<span style="font-family: inherit;">It&#8217;s reasonable to think that this may be there and I&#8217;m just missing it, since I am admittedly a novice in the SDN world, but if by chance I have not missed it because it&#8217;s not there, it needs to be addressed.  </span>  
<span style="font-family: inherit;"><br /> </span>

<div>
  [[ This is a content summary only. Visit my website for full links, other content, and more! ]]
</div>