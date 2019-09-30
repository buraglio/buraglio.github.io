---
id: 1024
title: 'NIX4NetEng #3 &#8211; Tracing paths'
date: 2014-06-07T13:43:21-06:00
author: Nick Buraglio
layout: post
guid: http://www.forwardingplane.net/?p=1024
permalink: /?p=1024
themeblvd_noindex:
  - 'true'
categories:
  - NIX4NetEng
---
Another useful bit of information is the path. Traceroute is fine, but it&#8217;s a bit of a &#8220;one and done&#8221; kind of tool. I prefer to use mtr because it can run for any amount of time I need it to and keep the statistics for the entire time viewable. It does require socket access, so you&#8217;ll either need root or sudo in most cases.

<pre>(~) jumphost $ sudo mtr 192.80.96.88 will yield the following table</pre>

[<img alt="Screenshot 2014-05-31 14.54.33" src="http://www.forwardingplane.net/wp-content/uploads/2014/05/Screenshot-2014-05-31-14.54.33.png" width="442" height="284" />](http://www.forwardingplane.net/wp-content/uploads/2014/05/Screenshot-2014-05-31-14.54.33.png)

&nbsp;

<div class="sharedaddy sd-sharing-enabled">
  <div class="robots-nocontent sd-block sd-social sd-social-icon-text sd-sharing">
    <h3 class="sd-title">
      Share this:
    </h3>
    
    <div class="sd-content">
      <ul>
        <li class="share-twitter">
          <a rel="nofollow noopener noreferrer" data-shared="sharing-twitter-1024" class="share-twitter sd-button share-icon" href="http://www.forwardingplane.net/?p=1024&share=twitter" target="_blank" title="Click to share on Twitter"><span>Twitter</span></a>
        </li>
        <li class="share-email">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-email sd-button share-icon" href="http://www.forwardingplane.net/?p=1024&share=email" target="_blank" title="Click to email this to a friend"><span>Email</span></a>
        </li>
        <li class="share-print">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-print sd-button share-icon" href="http://www.forwardingplane.net/?p=1024" target="_blank" title="Click to print"><span>Print</span></a>
        </li>
        <li class="share-linkedin">
          <a rel="nofollow noopener noreferrer" data-shared="sharing-linkedin-1024" class="share-linkedin sd-button share-icon" href="http://www.forwardingplane.net/?p=1024&share=linkedin" target="_blank" title="Click to share on LinkedIn"><span>LinkedIn</span></a>
        </li>
        <li class="share-facebook">
          <a rel="nofollow noopener noreferrer" data-shared="sharing-facebook-1024" class="share-facebook sd-button share-icon" href="http://www.forwardingplane.net/?p=1024&share=facebook" target="_blank" title="Click to share on Facebook"><span>Facebook</span></a>
        </li>
        <li class="share-reddit">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-reddit sd-button share-icon" href="http://www.forwardingplane.net/?p=1024&share=reddit" target="_blank" title="Click to share on Reddit"><span>Reddit</span></a>
        </li>
        <li class="share-tumblr">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-tumblr sd-button share-icon" href="http://www.forwardingplane.net/?p=1024&share=tumblr" target="_blank" title="Click to share on Tumblr"><span>Tumblr</span></a>
        </li>
        <li class="share-pinterest">
          <a rel="nofollow noopener noreferrer" data-shared="sharing-pinterest-1024" class="share-pinterest sd-button share-icon" href="http://www.forwardingplane.net/?p=1024&share=pinterest" target="_blank" title="Click to share on Pinterest"><span>Pinterest</span></a>
        </li>
        <li class="share-pocket">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-pocket sd-button share-icon" href="http://www.forwardingplane.net/?p=1024&share=pocket" target="_blank" title="Click to share on Pocket"><span>Pocket</span></a>
        </li>
        <li class="share-end">
        </li>
      </ul>
    </div>
  </div>
</div>