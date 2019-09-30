---
id: 187
title: A day with only IPv6
date: 2012-12-13T11:55:13-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2012/12/172-revision-9/
permalink: /2012/12/172-revision-9/
---
IPv6 is coming.  Like SDN, we can&#8217;t ignore it.  Are you ready?  Are you apps ready?  I&#8217;ll wager the answer is no.  Mine aren&#8217;t.  I&#8217;ve been working on IPv6 for about 11 years, from early days of tunnels to full native IPv6 at home and at work.  In teaching the IPv6 workshop for internet2, one of the things that I always suggest is to have a dual stacked host and an IPv6 only host available for testing.  These can be virtual machines or physical host, the important detail is that that need to be something that is deployed and a known working configuration. Ideally they&#8217;re a mirror or an analog of a typical workstation and or server on your network.

I&#8217;ve been doing this for some time, but I must admit I&#8217;m a little ashamed that I&#8217;ve never tried to do this for my personal day to day workstation, only for one off testing.  Well, that ends now, and the results aren&#8217;t pretty.

<p style="text-align: center;">
  <a href="http://www.forwardingplane.net/wp-content/uploads/2012/12/noipv4.png"><img class="aligncenter  wp-image-183" title="noipv4" src="http://www.forwardingplane.net/wp-content/uploads/2012/12/noipv4.png" alt="" width="465" height="405" srcset="http://www.forwardingplane.net/wp-content/uploads/2012/12/noipv4.png 665w, http://www.forwardingplane.net/wp-content/uploads/2012/12/noipv4-300x261.png 300w, http://www.forwardingplane.net/wp-content/uploads/2012/12/noipv4-550x478.png 550w" sizes="(max-width: 465px) 100vw, 465px" /></a>
</p>

My every day workstation is a mac. So, to remain productive, I didn&#8217;t use my primary workstation, but instead I attempted to mirror it as closely as possible.  The chosen analog was a mac mini running MacOS 10.7.  It was immediately clear that this wasn&#8217;t going to be a fully functional workstation.

Right from the get go there was an issue.  IPv6 doesn&#8217;t do any options in the SLACC implementation that 90% of folks doing dual stack are going to use.  DHCPv6 is still not widely deployed, DHCPv6 relay isn&#8217;t available in a vast swath of network hardware and most folks are going to initially start with stateless auto config, at least until they realize it&#8217;s more or less unmanageable.  Translated: you have no DNS without explicitly setting it statically.

Yuck.  I strongly discourage statically assigning things.  It makes changes far more painful than they need to be, is a support nightmare at nearly any scale  and decentralizes control. However, I had to for this test.  Fine, an IPv6 resolver was added.

Next step, run patching.  Nope.  Apple doesn&#8217;t support patching via their automated process via IPv6.  Most of this should be served by Akamai, which does support v6 in many cases, but not this one.  I can&#8217;t even patch the workstation without either running my own IPv6 enabled patch service (which requires manual configuration of a host to utilize), using a thumb drive or IPv6 enabled network mapping to grab the patches or plumbing IPv4 into it.

After fighting through patching the host, I wanted to actually use it.  This was mostly an exercise in patience as well.  The google based services I used all just worked.  Searches, gmail, blogger, etc.  I didn&#8217;t notice any difference whatsoever. One interesting thing that I noticed right away was that many ads and images on pages I was able to surf to weren&#8217;t working at all.  Ad content providers are behind the curve on delivering over IPv6.  This surprised me a bit since this is a revenue stream that is going to grow, and they&#8217;re missing the boat.  The upside was that I didn&#8217;t need to look at a bunch of ads, potentially distracting images and marketing hype.

Many of my work services such as exchange aren&#8217;t yet IPv6 enabled, I knew that wasn&#8217;t going to work because it&#8217;s actually on my teams list to remedy, however, I gave it a try anyway.  No go on OWA.  No go on any of the exchange access whatsoever.  NTP sync worked just fine after adding in our NTP server, its been IPv6 ready for a very long time.

Luckily for me, most of what I do is CLI based and the equipment I need to get into and help maintain has been IPv6 enabled for years.  SSH on this mac worked with absolutely no issues, as expected.  It&#8217;s one of those nice things that I&#8217;d been using IPv6 for in a dual stacked environment for years and is essentially transparent.

I was able to work on this blog post, since [forwardingplane.net](http://www.forwardingplane.net) has been IPv6 compliant since it&#8217;s inception thanks to the hosting provider, [arp networks](http://www.arpnetworks.com).

Other services that I use regularly, are a mixed bag.  [Box.net](http://www.box.net) has no IPv6 support. [Dropbox](http://www.dropbox.com), which I expected to work since it is hosted in the amazon cloud, doesn&#8217;t but probably trivially could.  [Spideroak](https://spideroak.com) didn&#8217;t work with only IPv6.  [Crashplan](http://www.crashplan.com) didn&#8217;t work to the cloud or my NAS.  NAS was expected since it doesn&#8217;t do v6.  This is a frightening wake-up call.  Enabling IPv6 support into these every day apps should have been done from the beginning or at the very least before IPv6 day.

Some other things I noticed, my [2 NAS](http://www.amazon.com/D-Link-DNS-343-Network-Attached-Enclosure/dp/B0019VSU88) at home don&#8217;t do IPv6 at all.  The aging Dell powerconnect gig switch I have at home doesn&#8217;t do IPv6.  My [Sonicwall TZ 210 wireless-N](http://o-www.sonicwall.com/us/en/products/TZ_210.html) that I&#8217;ve been testing at home has no IPv6 support by default although I think there is Beta code that I&#8217;ve been trying to get my hands on.

My appleTV, however, does do IPv6 as do my Linux VMs, Windows 7 VM and host Linux system.  My normal gateway device, a [pfSense](http://www.pfsense.org) install running on a [PC Engines ALIX](http://pcengines.ch/alix.htm) board has done IPv6, correctly mind you, for years, either by code I hacked into it (in the early days) or fully supported by the project.  It supports dhcpv6 server, dhcpv6-pd from my upstream provider and SLAAC.  It also does IPv6 firewall functions better than most commercial firewall devices.

I&#8217;m 100% sure it&#8217;s just the tip of the iceberg. If you&#8217;re a networking professional and you&#8217;re not learning IPv6, you&#8217;re already 10 years behind.  Head in the sand won&#8217;t make it go away, it&#8217;s happening, just like SDN is happening.  In fact, they&#8217;ll [be happening together in some cases](http://www.openflow.org/wk/index.php/OpenFlow_1_2_proposal#IPv6_support).  Learning new things is fun, and IPv6 is a necessity.  You can hide behind NAT and existing allocations for a while, but believe me, you&#8217;re doing yourself a disservice as well as missing out on some cool stuff if you&#8217;re not talking about your IPv6 plans and learning about this inevitable reality.