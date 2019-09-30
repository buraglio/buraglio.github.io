---
id: 1592
title: EdgeOS weighted load balance
date: 2019-02-18T11:39:22-06:00
author: Nick Buraglio
layout: revision
guid: https://www.forwardingplane.net/2019/02/1589-revision-v1/
permalink: /2019/02/1589-revision-v1/
---
<pre class="wp-block-preformatted">set load-balance group LoadBalance_WAN interface  route-test initial-delay 15<br />
set load-balance group LoadBalance_WAN interface  route-test interval 5<br />
set load-balance group LoadBalance_WAN interface  route-test type ping target <br />
set load-balance group LoadBalance_WAN interface  weight 95 # weight based on more bandwidth <br />
set load-balance group LoadBalance_WAN interface  route-test initial-delay 15<br />
set load-balance group LoadBalance_WAN interface  route-test interval 5<br />
set load-balance group LoadBalance_WAN interface  route-test type ping target <br />
set load-balance group LoadBalance_WAN interface  weight 5 # weight based on less bandwidth</pre>