---
id: 291
title: Installing OwnCloud on CentOS
date: 2012-12-30T07:32:17-06:00
author: Nick Buraglio
layout: post
guid: http://www.forwardingplane.net/?p=291
permalink: /?p=291
themeblvd_noindex:
  - 'true'
categories:
  - Data Center
  - Musings
  - UNIX
---
<pre>wget http://dl.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm
wget http://rpms.famillecollet.com/enterprise/remi-release-6.rpm
yum -y install apache2 php5 php5-json php-xml php-mbstring php5-zip php5-gd
yum -y install php5-sqlite curl libcurl3 libcurl3-dev php5-curl php-pd</pre>

php5-sqlite isn&#8217;t available in the repos I use. I wasn&#8217;t able to find it elsewhere either. Per <a href="http://php.net/manual/de/sqlite.installation.php " target="_blank">this page</a>, I have to install it by source.

<pre>cd /etc/yum.repos.d/
wget http://download.opensuse.org/repositories/isv:ownCloud:community/CentOS_CentOS-6/isv:ownCloud:community.repo
yum install owncloud</pre>

<div class="sharedaddy sd-sharing-enabled">
  <div class="robots-nocontent sd-block sd-social sd-social-icon-text sd-sharing">
    <h3 class="sd-title">
      Share this:
    </h3>
    
    <div class="sd-content">
      <ul>
        <li class="share-twitter">
          <a rel="nofollow noopener noreferrer" data-shared="sharing-twitter-291" class="share-twitter sd-button share-icon" href="http://www.forwardingplane.net/?p=291&share=twitter" target="_blank" title="Click to share on Twitter"><span>Twitter</span></a>
        </li>
        <li class="share-email">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-email sd-button share-icon" href="http://www.forwardingplane.net/?p=291&share=email" target="_blank" title="Click to email this to a friend"><span>Email</span></a>
        </li>
        <li class="share-print">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-print sd-button share-icon" href="http://www.forwardingplane.net/?p=291" target="_blank" title="Click to print"><span>Print</span></a>
        </li>
        <li class="share-linkedin">
          <a rel="nofollow noopener noreferrer" data-shared="sharing-linkedin-291" class="share-linkedin sd-button share-icon" href="http://www.forwardingplane.net/?p=291&share=linkedin" target="_blank" title="Click to share on LinkedIn"><span>LinkedIn</span></a>
        </li>
        <li class="share-facebook">
          <a rel="nofollow noopener noreferrer" data-shared="sharing-facebook-291" class="share-facebook sd-button share-icon" href="http://www.forwardingplane.net/?p=291&share=facebook" target="_blank" title="Click to share on Facebook"><span>Facebook</span></a>
        </li>
        <li class="share-reddit">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-reddit sd-button share-icon" href="http://www.forwardingplane.net/?p=291&share=reddit" target="_blank" title="Click to share on Reddit"><span>Reddit</span></a>
        </li>
        <li class="share-tumblr">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-tumblr sd-button share-icon" href="http://www.forwardingplane.net/?p=291&share=tumblr" target="_blank" title="Click to share on Tumblr"><span>Tumblr</span></a>
        </li>
        <li class="share-pinterest">
          <a rel="nofollow noopener noreferrer" data-shared="sharing-pinterest-291" class="share-pinterest sd-button share-icon" href="http://www.forwardingplane.net/?p=291&share=pinterest" target="_blank" title="Click to share on Pinterest"><span>Pinterest</span></a>
        </li>
        <li class="share-pocket">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-pocket sd-button share-icon" href="http://www.forwardingplane.net/?p=291&share=pocket" target="_blank" title="Click to share on Pocket"><span>Pocket</span></a>
        </li>
        <li class="share-end">
        </li>
      </ul>
    </div>
  </div>
</div>