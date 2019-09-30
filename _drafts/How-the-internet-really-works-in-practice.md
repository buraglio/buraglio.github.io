---
id: 1111
title: How the internet really works in practice
date: 2014-12-28T08:22:13-06:00
author: Nick Buraglio
layout: post
guid: http://www.forwardingplane.net/?p=1111
permalink: /?p=1111
categories:
  - Musings
---
The <a href="http://en.wikipedia.org/wiki/Border_Gateway_Protocol" target="_blank">Border Gateway Protocol</a> (BGPv4) is the foundation of the modern internet. Without it we would still be in the information dark ages and interconnectivity as we know it would not exist. One would assume, quite incorrectly I might add, that this foundational protocol is robust, secure and optimally configured to shepherd us through the daily use of this critical resource. While BGP has the capability of being all of those things, in practice it&#8217;s really not done that way. This is not a new subject and certainly not the first time <a href="http://searchnetworking.techtarget.com/opinion/After-20-years-BGP-still-lacks-security-foundation" target="_blank">I&#8217;ve written about it</a>.  After reading the very excellent packet pushers series on how the internet works by <a href="http://packetpushers.net/author/rwhite/" target="_blank">Russ White</a>, I found that the <a href="http://packetpushers.net/routing-resilience-manifesto/" target="_blank">Routing resilience manifesto </a>is quite fantastic and should be consumed by anyone running a network that utilizes BGP, particularly eBGP, because since 1997 I&#8217;ve seen far more networks that don&#8217;t follow these practices than ones that do.

BGP is one of those mechanisms that is, unfortunately, often done as a set and forget task. And herein lies the problem. I choose to think of it as a policy framework]

<div class="sharedaddy sd-sharing-enabled">
  <div class="robots-nocontent sd-block sd-social sd-social-icon-text sd-sharing">
    <h3 class="sd-title">
      Share this:
    </h3>
    
    <div class="sd-content">
      <ul>
        <li class="share-twitter">
          <a rel="nofollow noopener noreferrer" data-shared="sharing-twitter-1111" class="share-twitter sd-button share-icon" href="http://www.forwardingplane.net/?p=1111&share=twitter" target="_blank" title="Click to share on Twitter"><span>Twitter</span></a>
        </li>
        <li class="share-email">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-email sd-button share-icon" href="http://www.forwardingplane.net/?p=1111&share=email" target="_blank" title="Click to email this to a friend"><span>Email</span></a>
        </li>
        <li class="share-print">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-print sd-button share-icon" href="http://www.forwardingplane.net/?p=1111" target="_blank" title="Click to print"><span>Print</span></a>
        </li>
        <li class="share-linkedin">
          <a rel="nofollow noopener noreferrer" data-shared="sharing-linkedin-1111" class="share-linkedin sd-button share-icon" href="http://www.forwardingplane.net/?p=1111&share=linkedin" target="_blank" title="Click to share on LinkedIn"><span>LinkedIn</span></a>
        </li>
        <li class="share-facebook">
          <a rel="nofollow noopener noreferrer" data-shared="sharing-facebook-1111" class="share-facebook sd-button share-icon" href="http://www.forwardingplane.net/?p=1111&share=facebook" target="_blank" title="Click to share on Facebook"><span>Facebook</span></a>
        </li>
        <li class="share-reddit">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-reddit sd-button share-icon" href="http://www.forwardingplane.net/?p=1111&share=reddit" target="_blank" title="Click to share on Reddit"><span>Reddit</span></a>
        </li>
        <li class="share-tumblr">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-tumblr sd-button share-icon" href="http://www.forwardingplane.net/?p=1111&share=tumblr" target="_blank" title="Click to share on Tumblr"><span>Tumblr</span></a>
        </li>
        <li class="share-pinterest">
          <a rel="nofollow noopener noreferrer" data-shared="sharing-pinterest-1111" class="share-pinterest sd-button share-icon" href="http://www.forwardingplane.net/?p=1111&share=pinterest" target="_blank" title="Click to share on Pinterest"><span>Pinterest</span></a>
        </li>
        <li class="share-pocket">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-pocket sd-button share-icon" href="http://www.forwardingplane.net/?p=1111&share=pocket" target="_blank" title="Click to share on Pocket"><span>Pocket</span></a>
        </li>
        <li class="share-end">
        </li>
      </ul>
    </div>
  </div>
</div>