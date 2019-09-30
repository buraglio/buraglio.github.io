---
id: 1447
title: 'Strategy Series: How do you view outside of your network?'
date: 2018-02-10T10:58:04-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2018/02/1441-revision-v1/
permalink: /2018/02/1441-revision-v1/
---
In the tradition of my [NIX4NetEng](https://www.forwardingplane.net/topics/nix4neteng/) series I&#8217;m going to dive deep into the world of strategy, and specifically into the strategy of how we look at and operate our networks, the data they generate and the analytics that are available (and often overlooked) in how networks are managed both long term and day-to-day. So, in the spirit of visibility, lets think about how typical networks are monitored. My guess is that you either already know, or will soon realize that v_isibility and testing across disparate networks is hard._ This is a <span style="text-decoration: underline;"><strong>big</strong></span> topic, so sit back, relax, get your feet up and prepare for a magical journey into the fun and fantastical world of network visibility!

<center>
  <br />
</center>

  
[via GIPHY](https://giphy.com/gifs/magic-krhB8ydCQiYZq)

I&#8217;m going to glaze over the low hanging fruit of SNMP monitoring &#8211; you have all of that right? Yes? Good. No?!?! Shame on you&#8230;I&#8217;l do another post of some of my [favorite tools](https://www.librenms.org/) soon and you can shamefully download them and set them up, head hung low (until they&#8217;re up monitoring and alerting, at which point you can raise your head up high!). Lets make a very, very bold assumption that you totally understand how your internal network works, you have graphing, up/down statistics, traffic baselines and visibility into [traffic flow](http://www.forwardingplane.net/2017/12/what-is-your-netflow-strategy/) and [configurations](http://www.forwardingplane.net/2017/10/configuration-backups-opportunity-automation-management/). Don&#8217;t worry, if you don&#8217;t have those things you can link to a few options here or wait and I&#8217;ll circle back around to them in later topics.

<h1 style="text-align: center;">
  <span style="color: #808080;"><em>&#8220;Visibility and testing across diverse networks is hard.&#8221;</em></span>
</h1>

OK, so visibility.

<img class="alignnone size-large" src="http://www.nickburaglio.com/wp-content/uploads/2015/09/day7.jpg" width="1132" height="348" /> 

Any network engineer with some experience under their belt has gotten the problem report of &#8220;the internet is down&#8221; or &#8220;the internet is slow&#8221;. Yup, we all know them, we all love them. We even had an internal joke at a previous employer of mine that we could &#8220;ping the internet&#8221;, in that we created a CNAME of &#8220;theinternet&#8221; for a host that had high uptime.

<pre>(~) heelflip $ ping theinternet
PING theinternet (10.142.143.167): 56 data bytes
64 bytes from 10.14.143.167: icmp_seq=0 ttl=54 time=0.794 ms
64 bytes from 10.14.143.167: icmp_seq=1 ttl=54 time=0.768 ms
64 bytes from 10.14.143.167: icmp_seq=2 ttl=54 time=0.734 ms
64 bytes from 10.14.143.167: icmp_seq=3 ttl=54 time=0.732 ms
64 bytes from 10.14.143.167: icmp_seq=4 ttl=54 time=0.758 ms
64 bytes from 10.14.143.167: icmp_seq=5 ttl=54 time=0.761 ms</pre>

Right, so you get the internal network. What about when you get to the part that you don&#8217;t control and can&#8217;t see into? That&#8217;s harder, but rest easy &#8211; there are a number of ways to go about gathering the necessary details. What should those data sources be? Let me throw down what I think are important to track to really understand what the heck is going on outside of your AS or sphere of influence.

  1. Paths to common destinations ([google](https://google.com), [servicenow](https://www.servicenow.com), [SalesForce)](https://www.salesforce.com)
  2. Route table for all peerings (if taking more than default and are using eBGP)
  3. Latency statistics from your site to common destinations (see 1.)
  4. Latency statistics from outside of your network to your site
  5. Latency (and possibly throughput) statistics to intermediary points across your typical paths
  6. External route table and path statistics
  7. Packet loss statistics

That&#8217;s a decent amount of data. How can this be done? Well, let me tell you, there are a few ways but drawing them all together can be a daunting task. This can be accomplished by looking at data produced by [smokeping](https://oss.oetiker.ch/smokeping/) or [owamp](https://github.com/perfsonar/owamp) with an SNMP graphing tool for interface stats and [BGPMon](https://bgpmon.net/) and Peermon for BGP information. An opensource product called [perfSonar](https://www.perfsonar.net/) rolls a lot of this together, but there are commercial packages such as [ThousandEyes](https://www.thousandeyes.com/) that offer these types of statistics across a large swath of the internet as well. [RIPE ATLAS](https://atlas.ripe.net/) has a great deal of statistics that can be easily queried  and has a large install base too. If you are a savvy coder you can grab some good information from the [RIPE ATLAS API](https://atlas.ripe.net/docs/api/v2/manual/). If you don&#8217;t have the resources, capability, or time to do that then there is an option for a turnkey solution. <a style="font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen-Sans, Ubuntu, Cantarell, 'Helvetica Neue', sans-serif;" href="https://www.thousandeyes.com">ThousandEyes</a> <span style="font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen-Sans, Ubuntu, Cantarell, 'Helvetica Neue', sans-serif;">has a strong offering and there is a great deal of information that they gather. They also have very good presence and availability of information about their product, most recently presenting at </span><a style="font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen-Sans, Ubuntu, Cantarell, 'Helvetica Neue', sans-serif;" href="http://techfieldday.com/appearance/thousandeyes-presents-at-networking-field-day-17/">Network Field Day 17</a> <span style="font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen-Sans, Ubuntu, Cantarell, 'Helvetica Neue', sans-serif;">(and historically at </span><a style="font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen-Sans, Ubuntu, Cantarell, 'Helvetica Neue', sans-serif;" href="http://techfieldday.com/appearance/thousandeyes-presents-at-networking-field-day-6/">NFD 6</a><span style="font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen-Sans, Ubuntu, Cantarell, 'Helvetica Neue', sans-serif;">, </span><a style="font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen-Sans, Ubuntu, Cantarell, 'Helvetica Neue', sans-serif;" href="http://techfieldday.com/appearance/thousandeyes-presents-at-networking-field-day-8/">NFD 8</a><span style="font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen-Sans, Ubuntu, Cantarell, 'Helvetica Neue', sans-serif;">, and </span><a style="font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen-Sans, Ubuntu, Cantarell, 'Helvetica Neue', sans-serif;" href="http://techfieldday.com/appearance/thousandeyes-presents-at-networking-field-day-12/">NFD 12).</a><span style="font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen-Sans, Ubuntu, Cantarell, 'Helvetica Neue', sans-serif;"> I was a delegate at NFD 17 and was pleased to see another tool that provides visibility into BGP, a very often overlooked and yet </span><span style="font-family: -apple-system, system-ui, 'Segoe UI', Roboto, Oxygen-Sans, Ubuntu, Cantarell, 'Helvetica Neue', sans-serif;">unbelievably</span><span style="font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen-Sans, Ubuntu, Cantarell, 'Helvetica Neue', sans-serif;"> critical and useful viewpoint which has historically been difficult to see outside of tools like </span><a style="font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen-Sans, Ubuntu, Cantarell, 'Helvetica Neue', sans-serif;" href="http://www.forwardingplane.net/2015/03/opendns-acquires-bgpmon-and-the-future-of-route-monitoring/">BGPMon</a><span style="font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen-Sans, Ubuntu, Cantarell, 'Helvetica Neue', sans-serif;">. (see my previous </span><a style="font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen-Sans, Ubuntu, Cantarell, 'Helvetica Neue', sans-serif;" href="https://www.forwardingplane.net/topics/nix4neteng/">NIX4NetEng</a> <a style="font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen-Sans, Ubuntu, Cantarell, 'Helvetica Neue', sans-serif;" href="http://www.forwardingplane.net/2014/03/bgp-tools-troubleshooting-and-monitoring-external-routing-in-a-nutshell/">post about BGP visibility</a><span style="font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen-Sans, Ubuntu, Cantarell, 'Helvetica Neue', sans-serif;">). </span><a style="font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen-Sans, Ubuntu, Cantarell, 'Helvetica Neue', sans-serif;" href="http://techfieldday.com/appearance/netbeez-presents-at-networking-field-day-9/">NetBeez</a> <span style="font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen-Sans, Ubuntu, Cantarell, 'Helvetica Neue', sans-serif;">also has a reasonable offering but last I have looked it doesn&#8217;t really do much outside of a network (admittedly I may be behind the curve with their product).</span>

If you&#8217;re interested in seeing or hearing some more about these products, I did a packet pushers podcast on perfSonar a few years ago which is dated as far as feeds and speeds, but still very relevant today, you can read the show notes and listen [here.](http://packetpushers.net/podcast/podcasts/show-163-open-source-perfsonar-finds-the-flaws-impacting-the-flows/) For more info on ThousandEyes you can check out the latest [NFD17](http://techfieldday.com/event/nfd17/) videos.







&nbsp;

The real point is that to really see the performance of your network and to fully understand the true user experience you need to have total visibility into the entire ecosystem, not just the pieces that you can control.

###### 

###### *For anyone wigged out about the eyeball pic, those are my eyes [7 days after Lasik](http://www.nickburaglio.com/2015/09/02/eg-html/).