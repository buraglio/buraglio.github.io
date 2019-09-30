---
id: 1598
title: Comcast Business IPv6 Prefix Delegation
date: 2019-02-18T12:58:29-06:00
author: Nick Buraglio
layout: revision
guid: https://www.forwardingplane.net/2019/02/1597-revision-v1/
permalink: /2019/02/1597-revision-v1/
---
Comcast Business class service has some quirks when using the Cisco branded business gateway. Essentially, the prefix delegation will not work without very specific configuration options on the client. In order to run your own network border (i.e. not using their device as the first hop router for your LAN(s)), the following is required. In addition, with static IP addresses also comes with a static IPv6 prefix delegation. 

For Ubiquity EdgeOS (or a derivative like a Unifi USG) the following needs to be set (eth2 is the port facing the comcast router)

<pre class="wp-block-preformatted">set interfaces ethernet eth2 dhcpv6-pd prefix-only <br />set interfaces ethernet eth2 dhcpv6-pd rapid-commit disable </pre>

Mikrotik RouterOS

<pre class="wp-block-preformatted">/ipv6 dhcp-client<br />
add add-default-route=yes comment="Native Comcast IPv6 External" interface=ether2 pool-name=comcast-ipv6 pool-prefix-length=59 request=prefix use-peer-dns=no</pre>

Essentially, the trick is make sure you do the following: 

disable rapid-commit 

request a prefix-length of exactly 59

It won&#8217;t work any other way. Requesting an address (as opposed to an address+prefix or a different prefix hint essentially breaks the request.