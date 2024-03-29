---
id: 1601
title: Mikrotik IPv6 DHCPv6-PD configuration
date: 2019-02-18T13:26:52-06:00
author: Nick Buraglio
layout: revision
guid: https://www.forwardingplane.net/2019/02/1600-revision-v1/
permalink: /2019/02/1600-revision-v1/
---
For a small to medium ISPs (especially WISPs) looking to move to IPv6 dual-stack, the right way to deploy is to use DHCPv6 prefix delegation. Here is an example of how to do this in-skin (i.e. on the mikrotik itself rather than a relay). 

<pre class="wp-block-preformatted">/ipv6 dhcp-server<br /> add address-pool=vl100-v6-pd-pool interface=ether5.100 name=vl100-v6-pd<br /> add address-pool=vl101-v6-pd-pool interface=ether3.101 name=vl101-v6-pd<br /> add address-pool=vl102-v6-pd-pool interface=ether2.102 name=vl102-v6-pd<br /> add address-pool=vl106-v6-pd-pool interface=ether1.106 name=vl106-v6-pd<br /> add address-pool=vl108-v6-pd-pool interface=ether4.108 name=vl108-v6-pd</pre>

<pre class="wp-block-preformatted">/ipv6 pool<br />
add comment="VLAN103 IPv6 prefix delegation pool" name=vl103-v6-pd-pool prefix=2001:db8:1a:b000::/48 prefix-length=59<br />
add comment="VLAN100 IPv6 prefix delegation pool" name=vl100-v6-pd-pool prefix=2001:db8:1a:8800::/48 prefix-length=59<br />
add comment="VLAN101 IPv6 prefix delegation pool" name=vl101-v6-pd-pool prefix=2001:db8:1a:9000::/48 prefix-length=59<br />
add comment="VLAN106 IPv6 prefix delegation pool" name=vl106-v6-pd-pool prefix=2001:db8:1a:9800::/48 prefix-length=59<br />
add comment="VLAN108 IPv6 prefix delegation pool" name=vl108-v6-pd-pool prefix=2001:db8:1a:a000::/48 prefix-length=59<br />
add comment="VLAN102 IPv6 prefix delegation pool" name=vl102-v6-pd-pool prefix=2001:db8:1a:a800::/48 prefix-length=59</pre>

<pre class="wp-block-preformatted">/ipv6 address<br />
add address=2001:db8:1a:103::1 disabled=yes interface=bridge.103<br />
add address=2001:db8:1a:106::1 interface=ether1.106<br />
add address=2001:db8:1a:102::1 interface=ether2.102<br />
add address=2001:db8:1a:101::1 interface=ether3.101<br />
add address=2001:db8:1a:108::1 interface=ether4.108<br />
add address=2001:db8:1a:100::1 interface=ether5.100<br />
add address=2001:db8:1a:ffff::1/128 advertise=no comment=loopback0 interface=loopback.0<br />
add address=2001:db8:1a:fffe::2/127 advertise=no comment="point to point to tower1-gw" interface=ether7</pre>

Adjust firewall filters for IPv6 as policy dictates. Do not filter ICMP

<pre class="wp-block-preformatted">/ipv6 firewall filter<br /> add action=accept chain=forward comment="Allow all IPv6"</pre>

<pre class="wp-block-preformatted">/ipv6 nd<br />
add interface=ether5.100 managed-address-configuration=yes other-configuration=yes<br />
add interface=ether3.101 managed-address-configuration=yes other-configuration=yes<br />
add interface=ether2.102 managed-address-configuration=yes other-configuration=yes<br />
add interface=ether1.106 managed-address-configuration=yes other-configuration=yes<br />
add interface=ether4.108 managed-address-configuration=yes other-configuration=yes</pre>

<pre class="wp-block-preformatted">/ipv6 nd prefix<br />
add autonomous=no disabled=yes interface=ether5.100<br />
add autonomous=no disabled=yes interface=ether3.101<br />
add autonomous=no disabled=yes interface=ether2.102<br />
add autonomous=no disabled=yes interface=ether1.106<br />
add autonomous=no disabled=yes interface=ether4.108</pre>

<pre class="wp-block-preformatted">/ipv6 route<br />
add comment="IPv6 Default Route for static deployments" distance=1 gateway=fe80::2a7:42ff:fe2d:3574%bridge.10</pre>

Tunable based on deployment model  


<pre class="wp-block-preformatted">/ipv6 settings<br /> set max-neighbor-entries=1024</pre>