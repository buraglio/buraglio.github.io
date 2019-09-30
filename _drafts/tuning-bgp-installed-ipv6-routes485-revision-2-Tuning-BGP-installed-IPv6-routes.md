---
id: 487
title: Tuning BGP installed IPv6 routes
date: 2013-03-01T20:47:32-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2013/03/485-revision-2/
permalink: /2013/03/485-revision-2/
---
I&#8217;ve recently run into a situation where there was no longer enough space in the FIB to handle both the full IPv4 global table and the full IPv6 global table.  We prefer to run a default-free network within our RON, but in this case, until a hardware refresh can happen, we&#8217;ll need to adjust that.  Given what we knew about the size of both tables, it made more sense to take a default IPv6 route from one transit provider and filter the rest.  How we did this isn&#8217;t a groundbreaking marvel by any means, but it&#8217;s probably worth writing down for someone else to reference since it also applies to IPv4.

Since we already have global tables, a request to add IPv6 default to our existing full IPv6 table was made to one transit provider.  After that request was fulfilled, filter adjustments were made.  It should be note that all of these configs were generated off of Brocade MLX routers, so they may look a tad different than an IOS device.

Create a prefix list to reference that will allow default:

<pre>ipv6 prefix-list V6-PERMIT-DEFAULT seq 5 permit ::/0</pre>

Create the route map:

<pre>route-map ICCNv6-ATT-DEFAULT-IN permit 100
match ipv6 address prefix-list ICCNv6-PERMIT-DEFAULT</pre>

Before:

<pre>Neighbor Address AS#  State Time  Rt:Accepted Filtered Sent ToSend
2001:fd8:e00::2 65001 ESTAB 15d10h34m  12003    0       14    0</pre>

After:

<pre>Neighbor Address AS#  State Time  Rt:Accepted Filtered Sent ToSend
2001:fd8:e00::2 65001 ESTAB 15d10h34m     1    12002     14    0</pre>

Now we&#8217;ll need to filter the prefixes of every other peer to allow for only IPv6 routes sized /32 or larger:

<pre>route-map IPv6-BILAT-IN permit 100
 match ipv6 address prefix-list IPv6-PERMIT-ANY-32
 set community 65403:1425
 set local-preference 200 

ipv6 prefix-list IPv6-PERMIT-ANY-32 seq 5 permit ::/0 le 32</pre>