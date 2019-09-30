---
id: 1110
title: 'NIX4NetEng #5 &#8211; GeoIP tools'
date: 2014-12-21T12:21:44-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2014/12/1105-revision-v1/
permalink: /2014/12/1105-revision-v1/
---
Sometimes in networking and security it becomes necessary to do lookups of location data on IP addresses and prefixes.  
On my Mac I use <a href="http://brew.sh/" target="_blank">homebrew</a> to manage packages, but most of these tools are available with thetypocal apt, yum and port package management systems.

For this post, I&#8217;m going to shift gears and show the install on my mac:

<pre>sliver:~ buraglio$ brew install geoip
==&gt; Downloading https://downloads.sf.net/project/machomebrew/Bottles/geoip-1.6.3.mavericks.bottle.tar.gz
######################################################################## 100.0%
==&gt; Pouring geoip-1.6.3.mavericks.bottle.tar.gz
sliver:~ buraglio$ brew install geoipupdate
==&gt; Downloading https://downloads.sf.net/project/machomebrew/Bottles/geoipupdate-2.0.2.mavericks.bottle.tar.gz
######################################################################## 100.0%
==&gt; Pouring geoipupdate-2.0.2.mavericks.bottle.tar.gz</pre>

Once this installed we need to do a simple update:

<pre>sliver:~ buraglio$ geoipupdate
sliver:~ buraglio$</pre>

This really doesn&#8217;t yield any output, but I tend to do it pretty much every time I am using the tool so I know I have up to date information. So lets say that you are a service provider and your customers are calling complaining that they&#8217;re seeing www.weather.co.uk when going to weather.com or more realistically, they can&#8217;t get to netflix or amazon video, which tells them they don&#8217;t support srtreaming to the UK.

<pre>sliver:~ buraglio$ geoiplookup 141.142.2.2
GeoIP Country Edition: US, United States
GeoIP City Edition, Rev 1: US, IL, Illinois, Urbana, 61801, 40.109501, -88.212303, 648, 217</pre>

Nope, that looks ok, it must be something else [I have actually seen this problem in the past, it&#8217;s really no fun to run to ground]. As you can see, there is a good deal of information there, lat/long, area code, city, state, zip, etc. This data, specifically the lat/long, can be used to do really cool visualization stuff with things like google maps or google earth.

As a sanity check, here is a view of bbc.com:

<pre>sliver:~ buraglio$ geoiplookup 212.58.244.71
GeoIP Country Edition: GB, United Kingdom
GeoIP City Edition, Rev 1: GB, N7, Surrey, Tadworth, N/A, 51.283298, -0.233300, 0, 0</pre>

Yup, that looks right. The nice thing about this tool is that it can be automated to do all kinds of things with logs from syslog, Bro-IDS, Snort, whatever, and then act on the data or like I mentioned above, plot it out for visualization.

The one drawback I&#8217;ve found is that the IPv6 lookups are sparsely correct, for example:

<pre>sliver:~ buraglio$ geoiplookup6 2400:cb00:2048:1::681c:194f
sliver:~ buraglio$</pre>

Looking up 2400:cb00:2048:1::681c:194f which belongs to cloudflare yields me nothink, so there is some work to do there on the IPv6 front. Overall this is a useful tool for quick troubleshooting but it really shines when used in scripts and for visualization.