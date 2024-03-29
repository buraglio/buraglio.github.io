---
id: 263
title: CentOS sshguard install for limiting ssh scans
date: 2012-12-15T20:07:30-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2012/12/170-revision-7/
permalink: /2012/12/170-revision-7/
---
Securing SSH is a form or art.  It&#8217;s often debated, much like blocking all ICMP packets (which I normally disagree with).  If you need good proof, read [these](http://lonesysadmin.net/2012/11/20/changing-sshd-port-numbers-continues-to-be-a-bad-idea/) [posts](http://lonesysadmin.net/2012/10/19/on-using-alternate-ports-for-ssh/) by [Bob Plankers](https://twitter.com/plankers).  There is a camp that likes to promote moving to a non-standard port.  There is a faction that likes to block it completely except from a handful of hosts.  Then there are those that like to leave it open all together.  Running naked in the digital jungle.

I tend to err on the side of blocking except for jump hosts.  This is a pretty time proven methodology.  However, what about the hosts that **need** to be open? A hardened jump host or public shell box comes to mind.

Enter [sshguard](http://www.sshguard.net).

SSH Guard is an amazing little piece of software that takes the heavy lifting out of blocking all of those scans and automates removal of blocks.  It works across a myriad of popular unix platforms.

From <http://www.sshguard.net>:

_Sshguard monitors servers from their logging activity. When logs convey that someone is doing a Bad Thing, sshguard reacts by blocking he/she/it for a bit. Sshguard has a touchy personality: when a naughty tyke insists disturbing your host, it reacts firmer and firmer._

_Sshguard supports many services out of the box, recognizes severallog formats, and can operate many firewall systems. Many users appreciate its ease of use, compatibility and feature richness._

I like it because they have not left out some of the less common distros, but sinceI&#8217;ve mostly converted over to CentOS, this focus is how to set it up on Centos 6.4.   We&#8217;ll assume you have epel repo and rpmforge repo installed.

I prefer [syslog-ng](http://www.balabit.com/network-security/syslog-ng) so lets install that.

<pre>sudo yum -y install syslog-ng</pre>

<pre>chkconfig syslog-ng on</pre>

<pre>chkconfig rsyslog off</pre>

This isn&#8217;t necessary, but I&#8217;d recommend it.

Next, I lke to disable selinux.  It&#8217;s on be default in CentOS and I really don&#8217;t need what it offers.  I find it annoying and far too restrictive and this won&#8217;t build correctly without it disabled in my experience.

sudo vi /etc/selinux/config

    SELINUX=disabled

`Change the line that reads` 

    SELINUX=enabled

`to` 

    SELINUX=disabled

`You'll need to reboot to make this take effect.` 

Download sshguard.  I didn&#8217;t find it in any repos for Centos 6.x.  I may be mistaken, but I went this route.

<pre>wget http://sourceforge.net/projects/sshguard/files/sshguard/sshguard-1.5/sshguard-1.5.tar.bz2/download</pre>

Unpack it.

<pre>bunzip2 sshguard-1.5.tar.bz2</pre>

<pre>tar -xvf sshguard-1.5.tar</pre>

<pre>cd sshguard-1.5</pre>

I like to do minimal installs of Linux, so I need to add gcc before I can compile.  This will likely install some dependancies if it&#8217;s a new minimal install.  Same goes for make

<pre>sudo yum install gcc make</pre>

<pre>./configure --with-firewall=iptables</pre>

<pre>make && make install</pre>

&nbsp;