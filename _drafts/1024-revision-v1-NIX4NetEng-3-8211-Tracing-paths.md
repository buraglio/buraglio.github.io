---
id: 1025
title: 'NIX4NetEng #3 &#8211; Tracing paths'
date: 2014-06-07T13:43:21-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2014/06/1024-revision-v1/
permalink: /2014/06/1024-revision-v1/
---
Another useful bit of information is the path. Traceroute is fine, but it&#8217;s a bit of a &#8220;one and done&#8221; kind of tool. I prefer to use mtr because it can run for any amount of time I need it to and keep the statistics for the entire time viewable. It does require socket access, so you&#8217;ll either need root or sudo in most cases.

<pre>(~) jumphost $ sudo mtr 192.80.96.88 will yield the following table</pre>

[<img alt="Screenshot 2014-05-31 14.54.33" src="http://www.forwardingplane.net/wp-content/uploads/2014/05/Screenshot-2014-05-31-14.54.33.png" width="442" height="284" />](http://www.forwardingplane.net/wp-content/uploads/2014/05/Screenshot-2014-05-31-14.54.33.png)

&nbsp;