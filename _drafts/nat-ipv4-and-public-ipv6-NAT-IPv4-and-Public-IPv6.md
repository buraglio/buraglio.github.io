---
id: 51
title: NAT IPv4 and Public IPv6
date: 2010-09-10T17:51:00-06:00
author: Nick Buraglio
layout: post
guid: http://new.forwardingplane.net/2010/09/nat-ipv4-and-public-ipv6/
permalink: /?p=51
blogger_blog:
  - www.forwardingplane.net
blogger_author:
  - Nick Buraglio
blogger_permalink:
  - /feeds/3291015193216494208/posts/default/4906173773445147548
categories:
  - Uncategorized
---
I&#8217;ve recently taken to thinking a lot more about IPv6.  I&#8217;ve been using an [HE tunnel](http://www.tunnelbroker.net/) for as long as I can remember at home.  This poses an interesting question about addressing.  Since I have not had a public address block at home for almost 7 years, I have been using NAT for IPv4.  However, my IPv6 netblocks are a /64 and a /48, which are both far more address space than I could ever possibly use.  
There are more IPv4/IPv6 transitional mechanisms than a person could ever need, and keeping them straight, in addition to throwing an existing NAT IPv4 network (potentially a huge one) is tough.  
How are other large IPv4 deployments with NAT handling the inclusion of public IPv6 addresses?  One would guess that many of the sites are simply ignoring IPv6 until they absolutely have to use it.  Other sites may be deploying it in small pockets and not routing it offsite.  Yet other sites may be pushing it out and just making it a default deny inbound policy behind existing firewalls.  
Of those solutions, none really seem that appealing to me.  Maybe I need to shift my thinking about the public/private aspect of v4 in comparison to v6.  
To that end, how does one create tiered firewall groups for IPv6 (a topic for yet another set of poorly written notes)?

A few ideas that I&#8217;ve kicked around in my head were these:

1. No IPv6 (not really an option, but here for completeness)

2. IPv6 in a fully firewalled state (default deny inbound).  Not the greatest solution considering the additional headers in IPv6 and it&#8217;s native support for providing message authentication and integrity (AH) and message confidentiality and the integrity (ESP).

3. Different security models for the protocols (messy and hard to manage in the long run).

4.[ULA](http://en.wikipedia.org/wiki/Unique_local_address) (yuck; its not really 1918 space for IPv6 and doesn&#8217;t solve the off-the-site-connectivity problem anyway unless we use an [ALG](http://en.wikipedia.org/wiki/Application-level_gateway)).

[This](http://yorickdowne.wordpress.com/2010/01/15/ipv6-addressing-renumbering/) was an interesting read on a very similar subject.

<div class="sharedaddy sd-sharing-enabled">
  <div class="robots-nocontent sd-block sd-social sd-social-icon-text sd-sharing">
    <h3 class="sd-title">
      Share this:
    </h3>
    
    <div class="sd-content">
      <ul>
        <li class="share-twitter">
          <a rel="nofollow noopener noreferrer" data-shared="sharing-twitter-51" class="share-twitter sd-button share-icon" href="http://www.forwardingplane.net/?p=51&share=twitter" target="_blank" title="Click to share on Twitter"><span>Twitter</span></a>
        </li>
        <li class="share-email">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-email sd-button share-icon" href="http://www.forwardingplane.net/?p=51&share=email" target="_blank" title="Click to email this to a friend"><span>Email</span></a>
        </li>
        <li class="share-print">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-print sd-button share-icon" href="http://www.forwardingplane.net/?p=51" target="_blank" title="Click to print"><span>Print</span></a>
        </li>
        <li class="share-linkedin">
          <a rel="nofollow noopener noreferrer" data-shared="sharing-linkedin-51" class="share-linkedin sd-button share-icon" href="http://www.forwardingplane.net/?p=51&share=linkedin" target="_blank" title="Click to share on LinkedIn"><span>LinkedIn</span></a>
        </li>
        <li class="share-facebook">
          <a rel="nofollow noopener noreferrer" data-shared="sharing-facebook-51" class="share-facebook sd-button share-icon" href="http://www.forwardingplane.net/?p=51&share=facebook" target="_blank" title="Click to share on Facebook"><span>Facebook</span></a>
        </li>
        <li class="share-reddit">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-reddit sd-button share-icon" href="http://www.forwardingplane.net/?p=51&share=reddit" target="_blank" title="Click to share on Reddit"><span>Reddit</span></a>
        </li>
        <li class="share-tumblr">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-tumblr sd-button share-icon" href="http://www.forwardingplane.net/?p=51&share=tumblr" target="_blank" title="Click to share on Tumblr"><span>Tumblr</span></a>
        </li>
        <li class="share-pinterest">
          <a rel="nofollow noopener noreferrer" data-shared="sharing-pinterest-51" class="share-pinterest sd-button share-icon" href="http://www.forwardingplane.net/?p=51&share=pinterest" target="_blank" title="Click to share on Pinterest"><span>Pinterest</span></a>
        </li>
        <li class="share-pocket">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-pocket sd-button share-icon" href="http://www.forwardingplane.net/?p=51&share=pocket" target="_blank" title="Click to share on Pocket"><span>Pocket</span></a>
        </li>
        <li class="share-end">
        </li>
      </ul>
    </div>
  </div>
</div>