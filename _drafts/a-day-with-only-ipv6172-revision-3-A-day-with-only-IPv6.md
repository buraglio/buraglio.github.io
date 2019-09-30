---
id: 179
title: A day with only IPv6
date: 2012-12-13T10:23:51-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2012/12/172-revision-3/
permalink: /2012/12/172-revision-3/
---
IPv6 is coming.  Like SDN, we can&#8217;t ignore it.  Are you ready?  Are you apps ready?  I&#8217;ll wager the answer is no.  Mine aren&#8217;t.  I&#8217;ve been working on IPv6 for about 11 years, from early days of tunnels so full native IPv6 at home and at work.  In teaching the IPv6 workshop for internet2, one of the things that I always suggest is to have a dual stacked host and an IPv6 only host available for testing.  These can be virtual machines or physical host, the important detail is that that need to be something that is deployed and a known working configuration. Ideally they&#8217;re a mirror or an analog of a typical workstation and or server on your network.

I&#8217;ve been doing this for some time, but I must admit I&#8217;m a little ashamed that I&#8217;ve never tried to do this for my personal day to day workstation, only for one off testing.  Well, that ends now, and the results aren&#8217;t pretty.

My every day workstation is a mac. So, to remain productive, I didn&#8217;t use my primary workstation, but instead I attempted to mirror it as closely as possible.  The chosen analog was a mac mini running MacOS 10.7.  It was immediately clear that this wasn&#8217;t going to be a fully functional workstation.

Right from the get go there was an issue.  IPv6 doesn&#8217;t do any options in the SLACC implementation that 90% of folks doing dual stack are going to use.  DHCPv6 is still not widely deployed, DHCPv6 relay isn&#8217;t available in a vast swath of network hardware and most folks are going to initially start with stateless auto config, at least until they realize it&#8217;s more or less unmanageable.  Translated: you have no DNS without explicitly setting it statically.

Yuck.  I strongly discourage statically assigning things.  It makes changes far more painful than they need to be, is a support nightmare at nearly any scale  and decentralizes control. However, I had to for this test.  Fine, an IPv6 resolver was added.

Next step, run patching.  Nope.  Apple doesn&#8217;t support patching via their automated process via IPv6.  Most of this should be served by Akamai, which does support v6 in many cases, but not this one.  I can&#8217;t even patch the workstation without either running my own IPv6 enabled patch service (which requires manual configuration of a host to utilize), using a thumb drive or IPv6 enabled network mapping to grab the patches or plumbing IPv4 into it.

After fighting through patching the host, I wanted to actually use it.  This was mostly an exercise in patience as well.  The google based services I used all just worked.  Searches, gmail, blogger, etc.  I didn&#8217;t notice any difference whatsoever. One interesting thing that I noticed right away was that many ads and images on pages I was able to surf to weren&#8217;t working at all.  Ad content providers are behind the curve on delivering over IPv6.  This surprised me a bit since this is a revenue stream that is going to grow, and they&#8217;re missing the boat.  The upside was that I didn&#8217;t need to look at a bunch of ads, potentially distracting images and marketing hype.

Many of my work services such as exchange aren&#8217;t yet IPv6 enabled, I knew that wasn&#8217;t going to work because it&#8217;s actually on my teams list to remedy, however, I gave it a try anyway.  No go on OWA.  No go on any of the exchange access whatsoever.  NTP sync worked just fine after adding in our NTP server, its been IPv6 read.