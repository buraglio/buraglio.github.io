---
id: 269
title: CentOS sshguard install for limiting ssh scans
date: 2012-12-15T20:45:51-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2012/12/170-revision-13/
permalink: /2012/12/170-revision-13/
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

<pre>sudo vi /etc/selinux/config</pre>

Change the line that reads

    SELINUX=enabled

to

    SELINUX=disabled

You&#8217;ll need to reboot to make this take effect. Note that this will disable selinux completely and permanently.  [There are ways to temporarily disable it](http://www.revsys.com/writings/quicktips/turn-off-selinux.html) if you would prefer.

<pre>sudo reboot</pre>

Download sshguard.  I didn&#8217;t find it in any repos for Centos 6.x.  I may be mistaken, but I went this route.

<pre>wget http://sourceforge.net/projects/sshguard/files/sshguard/sshguard-1.5/sshguard-1.5.tar.bz2/download</pre>

Unpack it.

<pre>bunzip2 sshguard-1.5.tar.bz2</pre>

<pre>tar -xvf sshguard-1.5.tar</pre>

<pre>cd sshguard-1.5</pre>

I like to do minimal installs of Linux, so I need to add gcc before I can compile.  This will likely install some dependancies if it&#8217;s a new minimal install.  Same goes for make

<pre>sudo yum install gcc make</pre>

<pre>sudo ./configure --with-firewall=iptables</pre>

<pre>sudo make && sudo make install</pre>

OK, you should have it installed at this point.  You can verify by doing:

<pre>ls -la /usr/local/sbin/sshguard</pre>

which should yield something like this:

<pre>-rwxr-xr-x 1 root root 399995 Dec 16 02:28 /usr/local/sbin/sshguard</pre>

<pre></pre>

Great, now we need to create firewall tables for sshguard for IPv4, and if you&#8217;re keeping up to date, IPv6.

<pre>iptables -N sshguard
ip6tables -N sshguard</pre>

<pre></pre>

Now we need to activate it.  This is pretty straightforward.  We essentially need to tell syslog to call sshguard based on activity and it&#8217;s why I prefer syslog-ng.  It&#8217;s very flexible and easy to add this stuff right in.  I&#8217;ve been using it for over a decade and it the most flexible syslog server I&#8217;ve found.  

<pre>vi /etc/syslog-ng/syslog-ng.conf</pre>

Based on the [instructions at the sshguard site](http://www.sshguard.net/docs/setup/getlogs/syslog-ng/) (which also have details for extending this to more than just ssh; I&#8217;ll do a post on that for CentOS at some point too), just add the following to the bottom of your syslog-ng.conf file:

<pre># pass only entries with auth+authpriv facilities from programs other than sshguard</pre>

<pre>filter f_sshguard { facility(auth, authpriv) and not program("sshguard"); };</pre>

<pre># pass entries built with this format</pre>

<pre>destination sshguard {
 program("/usr/local/sbin/sshguard"
 template("$DATE $FULLHOST $MSGHDR$MESSAGE\n")
 );</pre>

<pre>};
log { source(s_sys); filter(f_sshguard); destination(sshguard); };</pre>

Then restart syslog-ng

<pre>sudo service syslog-ng stop</pre>

<pre>sudo service syslog-ng start</pre>

<div>
  You&#8217;ll probably see these errors, they can be ignored if you&#8217;re not using the afsql module.
</div>

<div>
</div>

<pre>Plugin module not found in 'module-path'; module-path='/lib64/syslog-ng', module='afsql'</pre>

<pre>Starting syslog-ng: Plugin module not found in 'module-path'; module-path='/lib64/syslog-ng', module='afsql'</pre>

&nbsp;