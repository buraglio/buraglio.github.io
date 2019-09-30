---
id: 614
title: Floodlight OpenFlow Firewall
date: 2013-04-27T17:24:39-06:00
author: Nick Buraglio
layout: post
guid: http://www.forwardingplane.net/?p=614
permalink: /?p=614
categories:
  - Musings
---
<pre>curl http://localhost:8080/wm/firewall/module/enable/json</pre>

<pre>curl http://localhost:8080/wm/firewall/module/status/json</pre>

Add allow rule:

<pre>curl -X POST -d '{"<a href="http://128.174.43.242:8080/switch/00:00:00:12:f2:91:58:00">00:00:00:12:f2:91:58:00</a>": "00:00:00:00:00:00:00:01"}' http://localhost:8080/wm/firewall/rules/json</pre>

<pre>http://docs.projectfloodlight.org/display/floodlightcontroller/Firewall+%28Dev%29</pre>

<div class="sharedaddy sd-sharing-enabled">
  <div class="robots-nocontent sd-block sd-social sd-social-icon-text sd-sharing">
    <h3 class="sd-title">
      Share this:
    </h3>
    
    <div class="sd-content">
      <ul>
        <li class="share-twitter">
          <a rel="nofollow noopener noreferrer" data-shared="sharing-twitter-614" class="share-twitter sd-button share-icon" href="http://www.forwardingplane.net/?p=614&share=twitter" target="_blank" title="Click to share on Twitter"><span>Twitter</span></a>
        </li>
        <li class="share-email">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-email sd-button share-icon" href="http://www.forwardingplane.net/?p=614&share=email" target="_blank" title="Click to email this to a friend"><span>Email</span></a>
        </li>
        <li class="share-print">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-print sd-button share-icon" href="http://www.forwardingplane.net/?p=614" target="_blank" title="Click to print"><span>Print</span></a>
        </li>
        <li class="share-linkedin">
          <a rel="nofollow noopener noreferrer" data-shared="sharing-linkedin-614" class="share-linkedin sd-button share-icon" href="http://www.forwardingplane.net/?p=614&share=linkedin" target="_blank" title="Click to share on LinkedIn"><span>LinkedIn</span></a>
        </li>
        <li class="share-facebook">
          <a rel="nofollow noopener noreferrer" data-shared="sharing-facebook-614" class="share-facebook sd-button share-icon" href="http://www.forwardingplane.net/?p=614&share=facebook" target="_blank" title="Click to share on Facebook"><span>Facebook</span></a>
        </li>
        <li class="share-reddit">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-reddit sd-button share-icon" href="http://www.forwardingplane.net/?p=614&share=reddit" target="_blank" title="Click to share on Reddit"><span>Reddit</span></a>
        </li>
        <li class="share-tumblr">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-tumblr sd-button share-icon" href="http://www.forwardingplane.net/?p=614&share=tumblr" target="_blank" title="Click to share on Tumblr"><span>Tumblr</span></a>
        </li>
        <li class="share-pinterest">
          <a rel="nofollow noopener noreferrer" data-shared="sharing-pinterest-614" class="share-pinterest sd-button share-icon" href="http://www.forwardingplane.net/?p=614&share=pinterest" target="_blank" title="Click to share on Pinterest"><span>Pinterest</span></a>
        </li>
        <li class="share-pocket">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-pocket sd-button share-icon" href="http://www.forwardingplane.net/?p=614&share=pocket" target="_blank" title="Click to share on Pocket"><span>Pocket</span></a>
        </li>
        <li class="share-end">
        </li>
      </ul>
    </div>
  </div>
</div>