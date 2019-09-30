---
id: 162
title: How I made a Sup2T-XL very unhappy
date: 2012-12-10T22:04:11-06:00
author: Nick Buraglio
layout: post
guid: http://www.forwardingplane.net/?p=162
permalink: /?p=162
categories:
  - Musings
---
Some people have a need to push hardware to it&#8217;s limits.  Generally, I end up being one of those people.  I must admit, I enjoy seeing how far things can be pushed, especially when it yields new and or interesting gains or knowledge.  One of the things that I needed to do was to rate limit a large set of addresses, but to allow unfettered access to other resources.  It&#8217;s possible there may be a better way to do this, but all of my other attempts to do this failed.  MicroFlow policing would kinda make it work, but the code to do so isn&#8217;t all in there yet for the SUP2T in either IOS 12.x or 15.0.  So, given few other choices we forged ahead with the plan to add ACLs, class maps and policy maps to make this work.

I knew we&#8217;d become resource strapped with this method, but until there was a better way, this was the path.  My IOS foo is admittedly  a tad weak these days working more on JunOS, so if these aren&#8217;t the optimal way to

&nbsp;

&nbsp;

<div class="sharedaddy sd-sharing-enabled">
  <div class="robots-nocontent sd-block sd-social sd-social-icon-text sd-sharing">
    <h3 class="sd-title">
      Share this:
    </h3>
    
    <div class="sd-content">
      <ul>
        <li class="share-twitter">
          <a rel="nofollow noopener noreferrer" data-shared="sharing-twitter-162" class="share-twitter sd-button share-icon" href="http://www.forwardingplane.net/?p=162&share=twitter" target="_blank" title="Click to share on Twitter"><span>Twitter</span></a>
        </li>
        <li class="share-email">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-email sd-button share-icon" href="http://www.forwardingplane.net/?p=162&share=email" target="_blank" title="Click to email this to a friend"><span>Email</span></a>
        </li>
        <li class="share-print">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-print sd-button share-icon" href="http://www.forwardingplane.net/?p=162" target="_blank" title="Click to print"><span>Print</span></a>
        </li>
        <li class="share-linkedin">
          <a rel="nofollow noopener noreferrer" data-shared="sharing-linkedin-162" class="share-linkedin sd-button share-icon" href="http://www.forwardingplane.net/?p=162&share=linkedin" target="_blank" title="Click to share on LinkedIn"><span>LinkedIn</span></a>
        </li>
        <li class="share-facebook">
          <a rel="nofollow noopener noreferrer" data-shared="sharing-facebook-162" class="share-facebook sd-button share-icon" href="http://www.forwardingplane.net/?p=162&share=facebook" target="_blank" title="Click to share on Facebook"><span>Facebook</span></a>
        </li>
        <li class="share-reddit">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-reddit sd-button share-icon" href="http://www.forwardingplane.net/?p=162&share=reddit" target="_blank" title="Click to share on Reddit"><span>Reddit</span></a>
        </li>
        <li class="share-tumblr">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-tumblr sd-button share-icon" href="http://www.forwardingplane.net/?p=162&share=tumblr" target="_blank" title="Click to share on Tumblr"><span>Tumblr</span></a>
        </li>
        <li class="share-pinterest">
          <a rel="nofollow noopener noreferrer" data-shared="sharing-pinterest-162" class="share-pinterest sd-button share-icon" href="http://www.forwardingplane.net/?p=162&share=pinterest" target="_blank" title="Click to share on Pinterest"><span>Pinterest</span></a>
        </li>
        <li class="share-pocket">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-pocket sd-button share-icon" href="http://www.forwardingplane.net/?p=162&share=pocket" target="_blank" title="Click to share on Pocket"><span>Pocket</span></a>
        </li>
        <li class="share-end">
        </li>
      </ul>
    </div>
  </div>
</div>