---
id: 317
title: DNS utilities on CentOS
date: 2013-01-03T22:41:47-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2013/01/316-revision/
permalink: /2013/01/316-revision/
---
It&#8217;s always annoying to me, being a convert from *BSD to Linux, that tools lke dig and host aren&#8217;t in the base install.  I realise that this makes me somewhat of a hypocrite, as I prefer an additive system rather than a subtractive base install.  Nevertheless, I&#8217;m continually surprised that &#8220;host&#8221; isn&#8217;t available after installing a minimal CentOS system without adding an additional package.  So, since I always forget, here is a quick blog post to remind me and any other converts how to install those tools:

&nbsp;

<pre>yum -y install bind-utils</pre>

<pre></pre>

That&#8217;s it.  Tragedy avoid.