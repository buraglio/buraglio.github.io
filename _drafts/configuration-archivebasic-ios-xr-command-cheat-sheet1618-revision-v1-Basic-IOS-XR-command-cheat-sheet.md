---
id: 1639
title: Basic IOS-XR command cheat sheet
date: 2019-03-15T20:08:09-06:00
author: Nick Buraglio
layout: revision
guid: https://www.forwardingplane.net/2019/03/1618-revision-v1/
permalink: /2019/03/1618-revision-v1/
---
Some basic commands that I have found useful in managing an ASR9K / IOS-XR device. This page is likely to grow and change over time.

Clear ARP

<pre class="wp-block-preformatted">clear arp-cache &lt;interface&gt; &lt;IPv4 addr&gt; location all </pre>

BGP

<pre class="wp-block-preformatted">show bgp all unicast summary </pre>

BGP Routes

<pre class="wp-block-preformatted"><br />show bgp ipv[4/6] unicast neighbors &lt;neighbor&gt; received route<br />show bgp ipv[4/6] unicast advertised neighbor &lt;neighbor&gt; <br />show bgp ipv[4/6] unicast summary<br />show bgp ipv[4/6] unicast summary<br />clear bgp ipv[4/6] unicast &lt;neighbor&gt; soft in<br />show bgp all unicast summary<br />show bgp ipv[4/6] unicast bestpath-compare</pre>

NetFlow

<pre class="wp-block-preformatted">show flow exporter <em>&lt;exporter&gt;</em> location 0/RSP0/CPU0 </pre>

Show all hardware linecards

<pre class="wp-block-preformatted">show hw-module fpd location all</pre>