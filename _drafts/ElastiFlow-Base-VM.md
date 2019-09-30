---
id: 1706
title: ElastiFlow Base VM
date: 2019-09-08T11:57:52-06:00
author: Nick Buraglio
layout: page
guid: http://www.forwardingplane.net/?page_id=1706
---
Included here is a vanilla Ubuntu 18 LTS VM with a basic [Elastiflow](https://github.com/robcowart/elastiflow) install. This includes all of the components of an ElasticStack plus the front end pieces of the ElastiFlow project. Most of the install is based on [this](https://www.catapultsystems.com/blogs/install-elastiflow-on-ubuntu-18-04-part-1/) how-to.&nbsp;

Included in the image is also a base install of NGINX and certbot so that you can reverse proxy the access and have a valid SSL certificate.&nbsp;

This was build and validated on Proxmox 6.0.6 but should be able to run on VMWare as well with a bit of qemu-img conversion. As expected, ElastiFlow (and ElasticStack) is fairly resource hungry, 16G of Memory and a handful of CPU cores is the bare minimum to run this with any real efficiency. Ubuntu 18 has changed how the networking is setup &#8211; it is all located in /etc/netplan/ now.     


Login Information:

<pre class="wp-block-preformatted">User Name: root
Password: elastiflow
Privileged user: elastiflow
Password: elastiflow<br /></pre>

Default IP addresses:

<pre class="wp-block-preformatted">10.255.255.5/27
2001:db8:ffff:2::5/64</pre>

Download the image [here](https://drive.google.com/open?id=1ga_Pj2j6h1ce9rcT7jQjncpVjLIC4X4t). 

<div class="sharedaddy sd-sharing-enabled">
  <div class="robots-nocontent sd-block sd-social sd-social-icon-text sd-sharing">
    <h3 class="sd-title">
      Share this:
    </h3>
    
    <div class="sd-content">
      <ul>
        <li class="share-twitter">
          <a rel="nofollow noopener noreferrer" data-shared="sharing-twitter-1706" class="share-twitter sd-button share-icon" href="http://www.forwardingplane.net/?page_id=1706&share=twitter" target="_blank" title="Click to share on Twitter"><span>Twitter</span></a>
        </li>
        <li class="share-email">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-email sd-button share-icon" href="http://www.forwardingplane.net/?page_id=1706&share=email" target="_blank" title="Click to email this to a friend"><span>Email</span></a>
        </li>
        <li class="share-print">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-print sd-button share-icon" href="http://www.forwardingplane.net/?page_id=1706" target="_blank" title="Click to print"><span>Print</span></a>
        </li>
        <li class="share-linkedin">
          <a rel="nofollow noopener noreferrer" data-shared="sharing-linkedin-1706" class="share-linkedin sd-button share-icon" href="http://www.forwardingplane.net/?page_id=1706&share=linkedin" target="_blank" title="Click to share on LinkedIn"><span>LinkedIn</span></a>
        </li>
        <li class="share-facebook">
          <a rel="nofollow noopener noreferrer" data-shared="sharing-facebook-1706" class="share-facebook sd-button share-icon" href="http://www.forwardingplane.net/?page_id=1706&share=facebook" target="_blank" title="Click to share on Facebook"><span>Facebook</span></a>
        </li>
        <li class="share-reddit">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-reddit sd-button share-icon" href="http://www.forwardingplane.net/?page_id=1706&share=reddit" target="_blank" title="Click to share on Reddit"><span>Reddit</span></a>
        </li>
        <li class="share-tumblr">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-tumblr sd-button share-icon" href="http://www.forwardingplane.net/?page_id=1706&share=tumblr" target="_blank" title="Click to share on Tumblr"><span>Tumblr</span></a>
        </li>
        <li class="share-pinterest">
          <a rel="nofollow noopener noreferrer" data-shared="sharing-pinterest-1706" class="share-pinterest sd-button share-icon" href="http://www.forwardingplane.net/?page_id=1706&share=pinterest" target="_blank" title="Click to share on Pinterest"><span>Pinterest</span></a>
        </li>
        <li class="share-pocket">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-pocket sd-button share-icon" href="http://www.forwardingplane.net/?page_id=1706&share=pocket" target="_blank" title="Click to share on Pocket"><span>Pocket</span></a>
        </li>
        <li class="share-end">
        </li>
      </ul>
    </div>
  </div>
</div>