---
id: 323
title: DNS utilities on CentOS
date: 2013-01-03T22:47:28-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2013/01/316-revision-7/
permalink: /2013/01/316-revision-7/
---
It&#8217;s always annoying to me, being a convert from *BSD to Linux, that tools lke dig and host aren&#8217;t in the minimal base install.  I realise that this makes me somewhat of a hypocrite, as I prefer an additive system rather than a subtractive base OS.  Nevertheless, I&#8217;m continually surprised that &#8220;host&#8221; isn&#8217;t available after installing a minimal CentOS system without adding an additional package.  So, since I always forget, here is a quick blog post to remind me and any other converts how to install those tools:

<pre> yum -y install bind-utils</pre>

<pre></pre>

That&#8217;s it.  Tragedy avoided.  Now I can make sure my AAAA records are working.

&nbsp;

<pre>[buraglio@cupcake httpd]# dig www.forwardingplane.net -t AAAA</pre>

<pre>; &lt;&lt;&gt;&gt; DiG 9.8.2rc1-RedHat-9.8.2-0.10.rc1.el6_3.6 &lt;&lt;&gt;&gt; www.forwardingplane.net -t AAAA
;; global options: +cmd
;; Got answer:
;; -&gt;&gt;HEADER&lt;&lt;- opcode: QUERY, status: NOERROR, id: 47725
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0</pre>

<pre>;; QUESTION SECTION:
;www.forwardingplane.net. IN AAAA</pre>

<pre>;; ANSWER SECTION:
www.forwardingplane.net. 86364 IN AAAA 2607:f2f8:4980::2</pre>

<pre>;; Query time: 1 msec
;; SERVER: 10.209.209.1#53(10.209.209.1)
;; WHEN: Thu Jan 3 22:49:35 2013
;; MSG SIZE rcvd: 69</pre>

&nbsp;