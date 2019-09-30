---
id: 176
title: CentOS sshguard install for limiting ssh scans
date: 2012-12-12T20:34:31-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2012/12/170-revision-2/
permalink: /2012/12/170-revision-2/
---
Securing SSH is a form or art.  It&#8217;s often debated, much like blocking all ICMP packets (which I normally disagree with).  If you need good proof, read [these](http://lonesysadmin.net/2012/11/20/changing-sshd-port-numbers-continues-to-be-a-bad-idea/) [posts](http://lonesysadmin.net/2012/10/19/on-using-alternate-ports-for-ssh/) by [Bob Plankers](https://twitter.com/plankers).  There is a camp that likes to promote moving to a non-standard port.  There is a faction that likes to block it completely except from a handful of hosts.  Then there are those that like to leave it open all together.  Running naked in the digital jungle.

I tend to err on the side of blocking except for jump hosts.  This is a pretty time proven methodology.  However, what about the hosts that **need** to be open? A hardened jump host or public shell box comes to mind.

Enter [sshguard](http://www.sshguard.net).

SSH Guard is an amazing little piece of software that takes the heavy lifting out of blocking all of those scans and automates removal of blocks.  It works across a myriad of popular unix platforms.

From <http://www.sshguard.net>:

<pre><em>Sshguard monitors servers from their logging activity. When logs convey that someone is doing a Bad Thing, sshguard reacts by blocking he/she/it for a bit. Sshguard has a touchy personality: when a naughty tyke insists disturbing your host, it reacts firmer and firmer.</em></pre>

<pre>Sshguard supports many services out of the box, recognizes severallog formats, and can operate many firewall systems. Many users appreciate its ease of use, compatibility and feature richness.</pre>

I like it because they have not left out some of the less common distros, but sinceI&#8217;ve mostly converted over to CentOS, this focus is how to set it up on Centos 6.4.   We&#8217;ll assume you have epel repo and rpmforge repo installed.

I prefer [syslog-ng](http://www.balabit.com/network-security/syslog-ng) so lets install that.

<pre>sudo yum -y install syslog-ng</pre>

<pre>chkconfig syslog-ng on</pre>

<pre>chkconfig rsyslog off</pre>

<pre>This</pre>

&nbsp;