---
id: 1596
title: Mikrotik Routed VLANs (non-CRS)
date: 2019-02-18T11:57:21-06:00
author: Nick Buraglio
layout: revision
guid: https://www.forwardingplane.net/2019/02/1595-revision-v1/
permalink: /2019/02/1595-revision-v1/
---
 

Add a simple set of VLANs to a CCR or other non-CRS RouterBoard. 



<pre class="wp-block-preformatted">/interface vlan <br />add interface=sfpplus1 name=sfpplus1.4 vlan-id=4 comment="VLAN ID 4"<br />add interface=sfpplus1 name=sfpplus1.5 vlan-id=5 comment="VLAN ID 5"<br />add interface=sfpplus1 name=sfpplus1.6 vlan-id=6 comment="VLAN ID 6"<br />add interface=sfpplus1 name=sfpplus1.7 vlan-id=7 comment="VLAN ID 7"<br />add interface=sfpplus1 name=sfpplus1.8 vlan-id=8 comment="VLAN ID 8"<br />add interface=sfpplus1 name=sfpplus1.9 vlan-id=9 comment="VLAN ID 9"</pre>

Add IP addressing to each VLAN

<pre class="wp-block-preformatted">/ipv6 address <br />add address=2001:db8:c33e:f0::1/64 advertise=no<br />add address=2001:db8:c:f4::1/64 advertise=yes interface=sfpplus1.4 <br />add address=2001:db8:c:f5::1/64 advertise=yes interface=sfpplus1.5 add address=2001:db8:c:f6::1/64 advertise=yes interface=sfpplus1.6 <br />add address=2001:db8:c:f7::1/64 advertise=yes interface=sfpplus1.7 <br />add address=2001:db8:c:f8::1/64 advertise=yes interface=sfpplus1.8 <br />add address=2001:db8:c:f9::1/64 advertise=yes interface=sfpplus1.9 </pre>

Add legacy IPv4 addressing for each VLAN

<pre class="wp-block-preformatted">/ip address<br />add address=10.2.200.1/26 interface=sfpplus1 comment="Native VLAN"<br />add address=10.2.4.1/25 interface=sfpplus1.4 <br />add address=10.2.5.1/25 interface=sfpplus1.5  <br />add address=10.2.6.1/25 interface=sfpplus1.6  <br />add address=10.2.7.1/25 interface=sfpplus1.7 <br />add address=10.2.8.1/25 interface=sfpplus1.8 <br />add address=10.2.9.1/25 interface=sfpplus1.9 </pre>