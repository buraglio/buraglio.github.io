---
id: 1374
title: The unrealized expectations of SDN
date: 2017-03-20T21:03:42-06:00
author: Nick Buraglio
layout: post
guid: http://www.forwardingplane.net/?p=1374
permalink: /?p=1374
categories:
  - Musings
---
I have been remiss in writing in the last year, the reasons are unimportant, but regardless, I&#8217;ve been paying very close attention. It&#8217;s 2017 and it is SOAPBOX time again!  SDN has been a &#8220;thing&#8221; since ~[2008](http://archive.openflow.org/documents/openflow-wp-latest.pdf), with the publication and popularization of the OpenFlow protocol. It&#8217;s 2017. How much has this industry changing technology is running outside of the hyper scale data centers?  We&#8217;ve seen companies rise and companies disappear. The promise of SDN is multi-faceted, but aside from automation and orchestration, the draw for many architects and engineers is the idea of modular control and data planes. The switching pieces in the data center work &#8211; for the most part. The promise of SDN may work for the hyperscalers &#8211; but what that does that mean for everyone else other than better cloud services? I&#8217;m going to discount enterprise, mostly, because enterprise, frankly, is slow to change and glacial when it comes to adopting new internal technologies, but that only serves to prove my point &#8211; it&#8217;s not there yet. That leaves my favorite subject: service providers &#8211; and I don&#8217;t mean SD-WAN (that&#8217;s something completely different and  don&#8217;t accept the name as correct).

The idea of taking a routing stack and a forwarding plane and breaking them apart, making them interchangeable and modular. This requires a few elemental attributes:

  * A strong routing stack including the venerable legacy protocols such as mBGP, IS-IS, LDP, etc.
  * Full support of the routed stack (IPv4 and IPv6)
  * A robust hardware platform with appropriate buffers
  * A way to couple the two in a stable and supportable way

This sounds simple. It&#8217;s not. Think about this from the perspective of the commercial UNIX systems of 20 years ago. The custom hardware did not always have compatibility with the software packages that the engineers needed to run on them. The implementations were clunky and sometimes half-done. Features didn&#8217;t always work. Updates were staggered, haphazard, and slow. This is what SDN has felt like for me for the past few years. Sure, if you&#8217;re in the data center and you want a single vendor solution &#8211; maybe. In my world that&#8217;s not ever the case, and I assert that if things don&#8217;t interoperate then they are incomplete. Where am I going with this rambling, nonsensical drivel? Hardware features and software features have a history of not matching when something is new and SDN has been the embodiment of that.

If I look back on the work I&#8217;ve done in the SDN space, and at the risk of being captain obvious, the lessons learned that come to mind from my experience designing, coordinating, building, and running actual production SDN networks are pretty easy to point out.

  * Centralized control doesn&#8217;t scale well geographically (or arguably at all).
  * Topology information is difficult to track in a timely manner in the WAN. See bullet 1. [<img class="alignright size-full wp-image-1378" src="http://www.forwardingplane.net/wp-content/uploads/2017/03/captain-obvious.jpg" alt="" width="234" height="215" />](http://www.forwardingplane.net/wp-content/uploads/2017/03/captain-obvious.jpg)
  * Re-inventing protocols stinks
  * Most of the issues revolve around scaling and support
  * Scaling is hard
  * All hardware is most certainly not created equally

The elephant in the room is that WAN gear is different. It&#8217;s historically been custom ASICs, sometimes FPGAs, and always has deep buffers. It also has a longer mean time before replacement. This is incongruent with the think buffered data center switches that most folks experiment with if they ever make it past [mininet](http://mininet.org/). Want to understand buffering and why it is necessary? Read up [here](https://people.ucsc.edu/~warner/buffer.html), it&#8217;s the best resource I&#8217;ve ever found on buffers of tons and tons of gear. The cliff&#8217;s notes are that when networks have a longer RTT, they need more buffering. TL/DR? Don&#8217;t use a freaking data center switch as your border router. Just because it _can_ run BGP doesn&#8217;t mean it _should_.

Now that I&#8217;ve seemingly called all of the babies ugly, let me shine a bit of light. I do have hope for some SDN. I think it exists now in the form of <a href="http://www.forwardingplane.net/2016/10/care-segment-routing/" target="_blank">segment routing</a>. Because we&#8217;ve seen the trying to turn an aircraft carrier on a dime is not easy, we can learn from it. There are a handful of solid SDN based WAN boxes out there and they bring strong offerings.

<div class="sharedaddy sd-sharing-enabled">
  <div class="robots-nocontent sd-block sd-social sd-social-icon-text sd-sharing">
    <h3 class="sd-title">
      Share this:
    </h3>
    
    <div class="sd-content">
      <ul>
        <li class="share-twitter">
          <a rel="nofollow noopener noreferrer" data-shared="sharing-twitter-1374" class="share-twitter sd-button share-icon" href="http://www.forwardingplane.net/?p=1374&share=twitter" target="_blank" title="Click to share on Twitter"><span>Twitter</span></a>
        </li>
        <li class="share-email">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-email sd-button share-icon" href="http://www.forwardingplane.net/?p=1374&share=email" target="_blank" title="Click to email this to a friend"><span>Email</span></a>
        </li>
        <li class="share-print">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-print sd-button share-icon" href="http://www.forwardingplane.net/?p=1374" target="_blank" title="Click to print"><span>Print</span></a>
        </li>
        <li class="share-linkedin">
          <a rel="nofollow noopener noreferrer" data-shared="sharing-linkedin-1374" class="share-linkedin sd-button share-icon" href="http://www.forwardingplane.net/?p=1374&share=linkedin" target="_blank" title="Click to share on LinkedIn"><span>LinkedIn</span></a>
        </li>
        <li class="share-facebook">
          <a rel="nofollow noopener noreferrer" data-shared="sharing-facebook-1374" class="share-facebook sd-button share-icon" href="http://www.forwardingplane.net/?p=1374&share=facebook" target="_blank" title="Click to share on Facebook"><span>Facebook</span></a>
        </li>
        <li class="share-reddit">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-reddit sd-button share-icon" href="http://www.forwardingplane.net/?p=1374&share=reddit" target="_blank" title="Click to share on Reddit"><span>Reddit</span></a>
        </li>
        <li class="share-tumblr">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-tumblr sd-button share-icon" href="http://www.forwardingplane.net/?p=1374&share=tumblr" target="_blank" title="Click to share on Tumblr"><span>Tumblr</span></a>
        </li>
        <li class="share-pinterest">
          <a rel="nofollow noopener noreferrer" data-shared="sharing-pinterest-1374" class="share-pinterest sd-button share-icon" href="http://www.forwardingplane.net/?p=1374&share=pinterest" target="_blank" title="Click to share on Pinterest"><span>Pinterest</span></a>
        </li>
        <li class="share-pocket">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-pocket sd-button share-icon" href="http://www.forwardingplane.net/?p=1374&share=pocket" target="_blank" title="Click to share on Pocket"><span>Pocket</span></a>
        </li>
        <li class="share-end">
        </li>
      </ul>
    </div>
  </div>
</div>