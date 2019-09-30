---
id: 336
title: Juniper EX4550 first impressions.
date: 2013-01-07T09:52:50-06:00
author: Nick Buraglio
layout: post
guid: http://www.forwardingplane.net/?p=336
permalink: /?p=336
themeblvd_noindex:
  - 'true'
categories:
  - Musings
---
Much less noise.  That was my initial thought when this box was first powered.  The 4500 sounds like a jet engine.  I was particularly excited about the Juniper EX4550 because it addressed a number of things that were less than ideal about the EX4500.

Soem of the differences ciuyld be argued as either oa pro or con depending on deployment scanerio, but for what we&#8217;re looking for, the 4550 is far better.

4550 Single PFE, 4500 dual PFE Single PFE being more desirable for us since cross box traffic doesn&#8217;t potentially need to transit across another PFE introducing a tad more latency.

\## Dual power supply in the 4550.  This one is a no brainer for us.  Redundancy is better.

32 line rate 1G/10G ports on the 4550.  40 on the 4500.  32 is plenty for us and is a worth while trade to get a single PFE.

Ours came with JUNOS 12.2R1.8.

root@EX-4550> show chassis hardware  
Hardware inventory:  
Item     Version     Part number Serial number Description  
Chassis LX0212450466 EX4550-32F  
Routing Engine 0 REV 12 750-045402 LX0212450466 EX4550-32F  
FPC 0 REV 12 750-045402 LX0212450466 EX4550-32F  
CPU BUILTIN BUILTIN FPC CPU  
PIC 0 BUILTIN BUILTIN 32x 1G/10G SFP/SFP+  
Xcvr 31 NON-JNPR AN07452H1V SFP-T  
Power Supply 0 REV 03 740-044332 1G032240641 JPSU-650W-AC-AFI  
Power Supply 1 REV 03 740-044332 1G032240660 JPSU-650W-AC-AFI  
Fan Tray Fan Module, Airflow In (AFI)

&nbsp;

<pre></pre>

&nbsp;

<div class="sharedaddy sd-sharing-enabled">
  <div class="robots-nocontent sd-block sd-social sd-social-icon-text sd-sharing">
    <h3 class="sd-title">
      Share this:
    </h3>
    
    <div class="sd-content">
      <ul>
        <li class="share-twitter">
          <a rel="nofollow noopener noreferrer" data-shared="sharing-twitter-336" class="share-twitter sd-button share-icon" href="http://www.forwardingplane.net/?p=336&share=twitter" target="_blank" title="Click to share on Twitter"><span>Twitter</span></a>
        </li>
        <li class="share-email">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-email sd-button share-icon" href="http://www.forwardingplane.net/?p=336&share=email" target="_blank" title="Click to email this to a friend"><span>Email</span></a>
        </li>
        <li class="share-print">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-print sd-button share-icon" href="http://www.forwardingplane.net/?p=336" target="_blank" title="Click to print"><span>Print</span></a>
        </li>
        <li class="share-linkedin">
          <a rel="nofollow noopener noreferrer" data-shared="sharing-linkedin-336" class="share-linkedin sd-button share-icon" href="http://www.forwardingplane.net/?p=336&share=linkedin" target="_blank" title="Click to share on LinkedIn"><span>LinkedIn</span></a>
        </li>
        <li class="share-facebook">
          <a rel="nofollow noopener noreferrer" data-shared="sharing-facebook-336" class="share-facebook sd-button share-icon" href="http://www.forwardingplane.net/?p=336&share=facebook" target="_blank" title="Click to share on Facebook"><span>Facebook</span></a>
        </li>
        <li class="share-reddit">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-reddit sd-button share-icon" href="http://www.forwardingplane.net/?p=336&share=reddit" target="_blank" title="Click to share on Reddit"><span>Reddit</span></a>
        </li>
        <li class="share-tumblr">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-tumblr sd-button share-icon" href="http://www.forwardingplane.net/?p=336&share=tumblr" target="_blank" title="Click to share on Tumblr"><span>Tumblr</span></a>
        </li>
        <li class="share-pinterest">
          <a rel="nofollow noopener noreferrer" data-shared="sharing-pinterest-336" class="share-pinterest sd-button share-icon" href="http://www.forwardingplane.net/?p=336&share=pinterest" target="_blank" title="Click to share on Pinterest"><span>Pinterest</span></a>
        </li>
        <li class="share-pocket">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-pocket sd-button share-icon" href="http://www.forwardingplane.net/?p=336&share=pocket" target="_blank" title="Click to share on Pocket"><span>Pocket</span></a>
        </li>
        <li class="share-end">
        </li>
      </ul>
    </div>
  </div>
</div>