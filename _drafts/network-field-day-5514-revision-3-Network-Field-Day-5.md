---
id: 517
title: Network Field Day 5
date: 2013-03-06T09:32:51-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2013/03/514-revision-3/
permalink: /2013/03/514-revision-3/
---
Last year, [Networking Field Day](http://techfieldday.com/event/nfd5/) was something that I&#8217;d heard of but wasn&#8217;t really aware of what is really was.  I occasionally looked at Twitter and saw the hash tags but did not know much about how it was set up or what it was about.  In fact, I actually thought it was supposed to be like the HAM radio field day stuff where you go out and build out an emergency network on the fly.  OK, I should have done more homework, admittedly.

Fast forward 6 months.

I&#8217;m working more and more with [Brent Salisbury](http://www.networkstatic.com) on day job stuff and he&#8217;s encouraging me to brush the dust off of my [old blog](http://www.forwardingplane.net) (which became this site). I&#8217;m working more on <a title="Building a Floodlight OpenFlow controller on CentOS 6" href="http://www.forwardingplane.net/2013/02/building-a-floodlight-openflow-controller-on-centos-6/" target="_blank">OpenFlow</a>,  virtualization stuff like <a title="CentOS KVM Install – Quick Start to a VM" href="http://www.forwardingplane.net/2013/03/centos-kvm-install-quick-start-to-a-vm/" target="_blank">KVM</a>, <a title="Headless VirtualBox host on CentOS" href="http://www.forwardingplane.net/2013/01/headless-virtualbox-host-on-centos/" target="_blank">VirtualBox</a> and <a href="http://www.vmware.com" target="_blank">VMware</a> and bringing up 100G WAN links.  I even had the extremely cool opportunity to do a [Packet Pushers Podcast](http://packetpushers.net/show-131-golf-cart-in-my-fibre-tunnel/).

Many of these things are a direct result of becoming more engaged in the larger community, a networking community I had pretty much carved myself out of back in 2002 when I left the service provider world for R&E.  This self isolation was a bit of an oversight on my part. What I did not realize was that, as someone in R&E, I had a unique perspective on some of the industry products and direction and was often seeing things a lot sooner than the general enterprise world.

As I got more and more engaged I realized that there were a **lot** of smart folks out there that like to collaborate, share and write about their professional experiences in our field of choice.  People that were doing innovative and interesting things that I didn&#8217;t know about.  <a href="http://techfieldday.com/event/nfd5/" target="_blank">NFD</a> was one of those things.  I started to write down more of the things I was thinking and doing.  I figured that at least someone would find them useful or interesting or at least fodder for solving insomnia.  When I was asked to participate and come out to NFD5, I was both ecstatic and humbled at the same time.  This was the place where the networking industry giants go to convene and discuss directionality as well as current networking technologies.  It&#8217;s the not unlike the oscars of packets and frames, high profile and filled with very well respected names.

Just to relay the scale and scope of the folks involved, here is the list:

&nbsp;

<table width="100%">
  <tr>
    <td rowspan="2" width="80" height="60">
      <a href="http://techfieldday.com/delegate/brandon-carroll/"><img title="http://techfieldday.com/wp-content/uploads/2012/08/Carroll-wpcf_60x60.jpeg" alt="http://techfieldday.com/wp-content/uploads/2012/08/Carroll-wpcf_60x60.jpeg" src="http://techfieldday.com/wp-content/uploads/2012/08/Carroll-wpcf_60x60.jpeg" /></a>
    </td>
    
    <td>
      <a href="http://techfieldday.com/delegate/brandon-carroll/">Brandon Carroll</a>
    </td>
    
    <td>
      <a href="http://twitter.com/BrandonCarroll">@BrandonCarroll</a>
    </td>
  </tr>
  
  <tr>
    <td colspan="2">
      CCIE Instructor, Blogger, and Technology Enthusiast
    </td>
  </tr>
  
  <tr>
    <td rowspan="2" width="80" height="60">
      <a href="http://techfieldday.com/delegate/brent-salisbury/"><img title="http://techfieldday.com/wp-content/uploads/2012/08/brent-salisbury1-wpcf_60x60.jpeg" alt="http://techfieldday.com/wp-content/uploads/2012/08/brent-salisbury1-wpcf_60x60.jpeg" src="http://techfieldday.com/wp-content/uploads/2012/08/brent-salisbury1-wpcf_60x60.jpeg" /></a>
    </td>
    
    <td>
      <a href="http://techfieldday.com/delegate/brent-salisbury/">Brent Salisbury</a>
    </td>
    
    <td>
      <a href="http://twitter.com/NetworkStatic">@NetworkStatic</a>
    </td>
  </tr>
  
  <tr>
    <td colspan="2">
      Brent Salisbury works as a Network Architect, CCIE #11972.
    </td>
  </tr>
  
  <tr>
    <td rowspan="2" width="80" height="60">
      <a href="http://techfieldday.com/delegate/colin-mcnamara/"><img title="http://techfieldday.com/wp-content/uploads/2012/08/cmcnamara-headshot-2011-color-scaled-wpcf_42x60.jpg" alt="http://techfieldday.com/wp-content/uploads/2012/08/cmcnamara-headshot-2011-color-scaled-wpcf_42x60.jpg" src="http://techfieldday.com/wp-content/uploads/2012/08/cmcnamara-headshot-2011-color-scaled-wpcf_42x60.jpg" /></a>
    </td>
    
    <td>
      <a href="http://techfieldday.com/delegate/colin-mcnamara/">Colin McNamara</a>
    </td>
    
    <td>
      <a href="http://twitter.com/ColinMcNamara">@ColinMcNamara</a>
    </td>
  </tr>
  
  <tr>
    <td colspan="2">
      Colin McNamara is a seasoned professional with over 15 years experience with network and systems technologies.
    </td>
  </tr>
  
  <tr>
    <td rowspan="2" width="80" height="60">
      <a href="http://techfieldday.com/delegate/ethan-banks/"><img title="http://techfieldday.com/wp-content/uploads/2012/08/ethan-banks-headshot-500x667-wpcf_44x60.jpg" alt="http://techfieldday.com/wp-content/uploads/2012/08/ethan-banks-headshot-500x667-wpcf_44x60.jpg" src="http://techfieldday.com/wp-content/uploads/2012/08/ethan-banks-headshot-500x667-wpcf_44x60.jpg" /></a>
    </td>
    
    <td>
      <a href="http://techfieldday.com/delegate/ethan-banks/">Ethan Banks</a>
    </td>
    
    <td>
      <a href="http://twitter.com/ECBanks">@ECBanks</a>
    </td>
  </tr>
  
  <tr>
    <td colspan="2">
      Ethan Banks, CCIE #20655, is a hands-on networking practitioner who has designed, built and maintained networks for higher education, state government, financial institutions, and technology corporations.
    </td>
  </tr>
  
  <tr>
    <td rowspan="2" width="80" height="60">
      <a href="http://techfieldday.com/delegate/greg-ferro/"><img title="http://techfieldday.com/wp-content/uploads/2012/08/Ferro-wpcf_60x39.jpg" alt="http://techfieldday.com/wp-content/uploads/2012/08/Ferro-wpcf_60x39.jpg" src="http://techfieldday.com/wp-content/uploads/2012/08/Ferro-wpcf_60x39.jpg" /></a>
    </td>
    
    <td>
      <a href="http://techfieldday.com/delegate/greg-ferro/">Greg Ferro</a>
    </td>
    
    <td>
      <a href="http://twitter.com/EtherealMind">@EtherealMind</a>
    </td>
  </tr>
  
  <tr>
    <td colspan="2">
      Over the last twenty odd years, Greg has worked Sales, Technical and IT Management but mostly he delivers Network Architecture and Design. Today he works as a Freelance Consultant for F100 companies in the UK & Europe focussing on Data Centres, Security and Operational Automation.
    </td>
  </tr>
  
  <tr>
    <td rowspan="2" width="80" height="60">
      <a href="http://techfieldday.com/delegate/john-herbert/"><img title="http://techfieldday.com/wp-content/uploads/2012/09/johnherbert-wpcf_60x60.jpeg" alt="http://techfieldday.com/wp-content/uploads/2012/09/johnherbert-wpcf_60x60.jpeg" src="http://techfieldday.com/wp-content/uploads/2012/09/johnherbert-wpcf_60x60.jpeg" /></a>
    </td>
    
    <td>
      <a href="http://techfieldday.com/delegate/john-herbert/">John Herbert</a>
    </td>
    
    <td>
      <a href="http://twitter.com/MrTugs">@MrTugs</a>
    </td>
  </tr>
  
  <tr>
    <td colspan="2">
      John has worked in the networking industry for 14 years, and obtained his CCIE Routing & Switching in early 2001.
    </td>
  </tr>
  
  <tr>
    <td rowspan="2" width="80" height="60">
      <a href="http://techfieldday.com/delegate/jon-langemak/"><img title="http://techfieldday.com/wp-content/uploads/2013/02/profile_picture-wpcf_52x60.jpg" alt="http://techfieldday.com/wp-content/uploads/2013/02/profile_picture-wpcf_52x60.jpg" src="http://techfieldday.com/wp-content/uploads/2013/02/profile_picture-wpcf_52x60.jpg" /></a>
    </td>
    
    <td>
      <a href="http://techfieldday.com/delegate/jon-langemak/">Jon Langemak</a>
    </td>
    
    <td>
      <a href="http://twitter.com/blinken_lichten">@blinken_lichten</a>
    </td>
  </tr>
  
  <tr>
    <td colspan="2">
      Jon Langemak is a Network Engineer, tech blogger, and dedicated tech enthusiast.
    </td>
  </tr>
  
  <tr>
    <td rowspan="2" width="80" height="60">
      <a href="http://techfieldday.com/delegate/josh-obrien/"><img title="http://techfieldday.com/wp-content/uploads/2012/08/OBrien-wpcf_60x60.jpeg" alt="http://techfieldday.com/wp-content/uploads/2012/08/OBrien-wpcf_60x60.jpeg" src="http://techfieldday.com/wp-content/uploads/2012/08/OBrien-wpcf_60x60.jpeg" /></a>
    </td>
    
    <td>
      <a href="http://techfieldday.com/delegate/josh-obrien/">Josh O’Brien</a>
    </td>
    
    <td>
      <a href="http://twitter.com/JoshOBrien77">@JoshOBrien77</a>
    </td>
  </tr>
  
  <tr>
    <td colspan="2">
      Josh has worked in the industry for 14 years and is now serving as CTO in the Telemedicine sector.
    </td>
  </tr>
  
  <tr>
    <td rowspan="2" width="80" height="60">
      <a href="http://techfieldday.com/delegate/paul-stewart/"><img title="http://techfieldday.com/wp-content/uploads/2012/08/IMG_0264-002-wpcf_60x60.jpg" alt="http://techfieldday.com/wp-content/uploads/2012/08/IMG_0264-002-wpcf_60x60.jpg" src="http://techfieldday.com/wp-content/uploads/2012/08/IMG_0264-002-wpcf_60x60.jpg" /></a>
    </td>
    
    <td>
      <a href="http://techfieldday.com/delegate/paul-stewart/">Paul Stewart</a>
    </td>
    
    <td>
      <a href="http://twitter.com/PacketU">@PacketU</a>
    </td>
  </tr>
  
  <tr>
    <td colspan="2">
      Paul Stewart is a Network and Security Engineer, Trainer and Blogger who enjoys understanding how things really work.
    </td>
  </tr>
  
  <tr>
    <td rowspan="2" width="80" height="60">
      <a href="http://techfieldday.com/delegate/pete-welcher/"><img title="http://techfieldday.com/wp-content/uploads/2013/02/DSC6539smaller2-wpcf_60x47.jpg" alt="http://techfieldday.com/wp-content/uploads/2013/02/DSC6539smaller2-wpcf_60x47.jpg" src="http://techfieldday.com/wp-content/uploads/2013/02/DSC6539smaller2-wpcf_60x47.jpg" /></a>
    </td>
    
    <td>
      <a href="http://techfieldday.com/delegate/pete-welcher/">Pete Welcher</a>
    </td>
    
    <td>
      <a href="http://twitter.com/pjwelcher">@pjwelcher</a>
    </td>
  </tr>
  
  <tr>
    <td colspan="2">
      Pete is a 15+ year CCIE who loves network design, and is currently avidly learning various datacenter technologies.
    </td>
  </tr>
  
  <tr>
    <td rowspan="2" width="80" height="60">
      <a href="http://techfieldday.com/delegate/terry-slattery/"><img title="http://techfieldday.com/wp-content/uploads/2012/08/Slattery-wpcf_60x50.jpg" alt="http://techfieldday.com/wp-content/uploads/2012/08/Slattery-wpcf_60x50.jpg" src="http://techfieldday.com/wp-content/uploads/2012/08/Slattery-wpcf_60x50.jpg" /></a>
    </td>
    
    <td>
      <a href="http://techfieldday.com/delegate/terry-slattery/">Terry Slattery</a>
    </td>
    
    <td>
    </td>
  </tr>
  
  <tr>
    <td colspan="2">
      Terry Slattery, CCIE #1026, is a senior network engineer with decades of experience in the internetworking industry.
    </td>
  </tr>
  
  <tr>
    <td rowspan="2" width="80" height="60">
      <a href="http://techfieldday.com/delegate/tom-hollingsworth/"><img title="http://techfieldday.com/wp-content/uploads/2012/08/bwry5mviq6ss0pe6m517-wpcf_46x60.png" alt="http://techfieldday.com/wp-content/uploads/2012/08/bwry5mviq6ss0pe6m517-wpcf_46x60.png" src="http://techfieldday.com/wp-content/uploads/2012/08/bwry5mviq6ss0pe6m517-wpcf_46x60.png" /></a>
    </td>
    
    <td>
      <a href="http://techfieldday.com/delegate/tom-hollingsworth/">Tom Hollingsworth</a>
    </td>
    
    <td>
      <a href="http://twitter.com/NetworkingNerd">@NetworkingNerd</a>
    </td>
  </tr>
  
  <tr>
    <td colspan="2">
      Tom Hollingsworth, CCIE #29213, is a Senior Solutions Architect for a small VAR focusing primarily on K-12 education.
    </td>
  </tr>
</table>

The list of vendor participants is also deep.  <a href="http://www.cisco.com" target="_blank">Cisco</a>, <a href="http://www.juniper.net" target="_blank">Juniper</a>, <a href="http://www.ruckuswireless.com" target="_blank">Ruckus Wireless</a>, <a href="www.plexxi.com/" target="_blank">Plexxi</a>, <a href="www.brocade.com/" target="_blank">Brocade</a> and <a href="http://www.solarwinds.com" target="_blank">SolarWinds</a> are all on the docket.

Unfortunately, I was not able to attend due to work scheduling and coordination of family stuff, something I truly lament.  To think that I was considered to be on that list is truly humbling and .  I wanted to participate as much as I could, so I started looking around and talking to folks and found the link to the live feed as well as the Twitter hashtag.

&nbsp;