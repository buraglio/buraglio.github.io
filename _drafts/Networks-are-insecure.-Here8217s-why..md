---
id: 1409
title: 'Networks are insecure. Here&#8217;s why.'
date: 2017-07-22T11:27:35-06:00
author: Nick Buraglio
layout: post
guid: http://www.forwardingplane.net/?p=1409
permalink: /?p=1409
categories:
  - Musings
---
Networks are insecure, they just are. I once worked with an FBI agent who said that if you wanted a secure network you should turn everything off, smash it, then set it on fire &#8211; and I don&#8217;t disagree. However, there are things we can do to understand our networks that will aid immeasurably in how they are secured and initially and how they remain secured over time.

At their very core networks are not secure based simply on the fact that humans are involved in their construction, operation, and use.  Recently, ICS-CERT released their annual report detailing the state of critical infrastructure and their report details exactly what anyone in the trenches should already know: **we don&#8217;t pay enough attention to this stuff**.  Their assessment pointed out some pretty glaring holes, most of which we probably already knew (or should have) and some of which we may need to spend time learning about. In our never-ending quest for convenient, ubiquitous access to all things, we often forget to think about the little things, the &#8220;dirty jobs&#8221; of IT. Ive said it so many times I&#8217;m almost sick of hearing it myself: **building a network is easy, running a network is hard.** Strip away all of the shiny, hype machine, marketing generated razzmatazz surrounding all things &#8220;cloud&#8221; and &#8220;SDN&#8221; and &#8220;intent-driven&#8221;. Those things are great and I&#8217;m neck deep in a lot of them, but building fancy things on broken foundations is clearly a bad idea, and a lot of what I see in the trenches is just that: broken, neglected, outdated, or just plain done poorly or done well and never maintained. When most people think about maintaining a network ecosystem they probably imagine plumbing vlans, changing peerings, creating LSPs or adjusting switchports. Realistically, that&#8217;s a tiny part of operations. In reality, most network issues could either be more easily solved by better understanding of a complex system or, in many cases, avoided completely by **knowing your network**. When I say &#8220;avoided completely&#8221;, what I mean is that be knowing the baseline of something you can identify deviations from that baseline which can indicate an issue that needs to be addresses. It&#8217;s no secret that I fiormly believe that the key to operating anything in IT is complete visibility and baselining of every facet that can be recorded, and I also assert that you cannot secure something until you truly understand not only how it works but how it fails. Anything less is an exercise in risk management. So, to that end, I will give a brief outline of what I believe is a foundation that we should all start from when building network analytics and monitoring.

&nbsp;

A gigantic swath of this issue can be alleviated be three things: Knowing your network, Access control of your network, and attention to your network

  * Network flow data (netflow, jflow, sflow, ipfix)
  * Centralized logging of \*all\* devices on the network
  * Traffic statistics (interface counters, error counters, etc.)
  * Configuration management of all network devices
  * Template configurations for all commonly configured items (common firewall filters, RE filtering, apply groups, ZTP, VM templates, etc.)
  * DNS query data
  * Latency and jitter information to/from all key locations in the network, including ingress/egress of the network
  * Routing table information (IGP and EGP)
  * optical power readings
  * hardware inventory (linecards, serial numbers, chassis models)
  * Environmental data (heat, power, cooling)
  * Full packet capture at network egress (if possible &#8211; ISPs obviously cannot realistically do this)
  * Anomalous policy / signature detection at all strategic locations

OK, now you have the firehose. That&#8217;s actually the easy part. Now, once you have this data you have to keep it up to date and keep watching it. Given the nature of what it is, you&#8217;re likely going to have to visit several systems to monitor it. There are some &#8220;meta&#8221; packages that can do a lot of it, librenms can tie together a bunch of these elements, as cam

<div class="sharedaddy sd-sharing-enabled">
  <div class="robots-nocontent sd-block sd-social sd-social-icon-text sd-sharing">
    <h3 class="sd-title">
      Share this:
    </h3>
    
    <div class="sd-content">
      <ul>
        <li class="share-twitter">
          <a rel="nofollow noopener noreferrer" data-shared="sharing-twitter-1409" class="share-twitter sd-button share-icon" href="http://www.forwardingplane.net/?p=1409&share=twitter" target="_blank" title="Click to share on Twitter"><span>Twitter</span></a>
        </li>
        <li class="share-email">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-email sd-button share-icon" href="http://www.forwardingplane.net/?p=1409&share=email" target="_blank" title="Click to email this to a friend"><span>Email</span></a>
        </li>
        <li class="share-print">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-print sd-button share-icon" href="http://www.forwardingplane.net/?p=1409" target="_blank" title="Click to print"><span>Print</span></a>
        </li>
        <li class="share-linkedin">
          <a rel="nofollow noopener noreferrer" data-shared="sharing-linkedin-1409" class="share-linkedin sd-button share-icon" href="http://www.forwardingplane.net/?p=1409&share=linkedin" target="_blank" title="Click to share on LinkedIn"><span>LinkedIn</span></a>
        </li>
        <li class="share-facebook">
          <a rel="nofollow noopener noreferrer" data-shared="sharing-facebook-1409" class="share-facebook sd-button share-icon" href="http://www.forwardingplane.net/?p=1409&share=facebook" target="_blank" title="Click to share on Facebook"><span>Facebook</span></a>
        </li>
        <li class="share-reddit">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-reddit sd-button share-icon" href="http://www.forwardingplane.net/?p=1409&share=reddit" target="_blank" title="Click to share on Reddit"><span>Reddit</span></a>
        </li>
        <li class="share-tumblr">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-tumblr sd-button share-icon" href="http://www.forwardingplane.net/?p=1409&share=tumblr" target="_blank" title="Click to share on Tumblr"><span>Tumblr</span></a>
        </li>
        <li class="share-pinterest">
          <a rel="nofollow noopener noreferrer" data-shared="sharing-pinterest-1409" class="share-pinterest sd-button share-icon" href="http://www.forwardingplane.net/?p=1409&share=pinterest" target="_blank" title="Click to share on Pinterest"><span>Pinterest</span></a>
        </li>
        <li class="share-pocket">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-pocket sd-button share-icon" href="http://www.forwardingplane.net/?p=1409&share=pocket" target="_blank" title="Click to share on Pocket"><span>Pocket</span></a>
        </li>
        <li class="share-end">
        </li>
      </ul>
    </div>
  </div>
</div>