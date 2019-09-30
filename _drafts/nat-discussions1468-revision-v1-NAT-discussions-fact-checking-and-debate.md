---
id: 1469
title: NAT discussions, fact checking, and debate
date: 2018-06-11T03:41:15-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2018/06/1468-revision-v1/
permalink: /2018/06/1468-revision-v1/
---
I’ve been very vocal about the misinterpretation of NAT for many, many years. Since it&#8217;s inception, NAT has been slowly perverted into what many now believe to be a security mechanism. While I do see a reasonable use of IP masquerading in a larger security strategy, this is not the original intent (or implementation) of NAT. What mosts network engineers call &#8220;NAT&#8221; is actually [one to many network port address translation](https://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/ipmasq-background2.1.html) &#8211; or taking one public address and &#8220;hiding&#8221; a number of private (likely [RFC1918](https://tools.ietf.org/html/rfc1918)) addresses &#8220;behind&#8221; it, using ports to translate traffic and keeping the state of those connections. Given my&#8230;.vigor for debating the details of NAT, I was invited to discuss this on [an episode of The Network Collective Podcast.](https://thenetworkcollective.com/2018/05/ep28-for-the-love-of-nat/) We get to some of the grimy details with some technical heavy hitters, so if you&#8217;re into the debate, it is certainly worth a watch.