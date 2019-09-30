---
id: 645
title: MPLS PseudoWire (VLL) between JunOS and Brocade MLX/XMR
date: 2013-05-17T10:22:54-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2013/05/644-revision/
permalink: /2013/05/644-revision/
---
I love to be the &#8220;uncola&#8221; of networking sites.  I like interop and I don&#8217;t do a lot with Cisco because I don&#8217;t have access to much of their gear anymore.  So, that being the case, I had a need to bring up a l2circuit (in JunOS speak), or VLL (in Brocade speak) between an MX480 and an MLX.  Since they are very different platforms, I had to do some digging and playing around to get it to work.  
You should have a rudimentary understanding of MPLS (which is about what I have) to do this.  
For the

JunOS:

<pre>set protocols l2circuit neighbor interface virtual-circuit-id
set protocols l2circuit neighbor interface encapsulation-type ethernet

set interfaces xe-3/3/0 description
set interfaces xe-3/3/0 vlan-tagging
set interfaces xe-3/3/0 encapsulation flexible-ethernet-services
set interfaces xe-3/3/0 unit encapsulation vlan-ccc
set interfaces xe-3/3/0 unit vlan-id</pre>

Brocade:

<pre>MLX1#show mpls config
router mpls
policy
no propagate-ttl

mpls-interface e1/1
ldp-enable

mpls-interface e1/4
ldp-enable

vll TEST-ICCN-VLL-1 raw-mode
vll-peer
vlan
tagged e 5/2</pre>

Some helpful commands:

JunOS:  
Useful for debugging connections that won&#8217;t come up:

<pre>set protocols l2circuit traceoptions file l2-VLL
set protocols l2circuit traceoptions file size 20240
set protocols l2circuit traceoptions flag all</pre>

Brocade:

<pre>logging console
terminal monitor
debug mpls all
debug mpls ldp</pre>

Show commands:

JunOS:  
check end to end l2circuit / VLL connectivity

<pre>ping mpls l2circuit interface &lt;interface.unit> detail</pre>

Show detail of l2circuit / pseudowire / vll  
show interfaces <interface.unit> extensive # or detail  
Brocade

<pre>show VLL detail <VLL id></p>


<pre>