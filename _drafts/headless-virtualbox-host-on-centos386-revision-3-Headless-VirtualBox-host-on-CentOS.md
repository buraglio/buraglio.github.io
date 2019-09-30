---
id: 399
title: Headless VirtualBox host on CentOS
date: 2013-01-29T15:16:18-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2013/01/386-revision-3/
permalink: /2013/01/386-revision-3/
---
Starting from a base CentOS system with nothing configured, and referencing the <a href="http://wiki.centos.org/HowTos/Virtualization/VirtualBox" target="_blank">CentOS wiki</a>, here is how I like to set up a headless virtualbox environment:

Disable selinux. It&#8217;s overly cumbersome and is enabled by default in CentOS.  I like to permanently disable it even though the default is permissive.  I ride the edge, I know.

<pre>vi /etc/selinux/config</pre>

<div>
   and change
</div>

<pre>SELINUX=enabled</pre>

<div>
  to
</div>

<pre>SELINUX=disabled</pre>

<div>
  Then reboot.
</div>

Using the methodology I originally found found <a href="http://stackoverflow.com/questions/14016286/how-to-programmatically-install-the-latest-epel-release-rpm-without-knowing-its" target="_blank">here</a>, I like to install the epel repo using this method:

<pre>cat &lt;&lt;EOM &gt;/etc/yum.repos.d/epel-bootstrap.repo
 [epel]
 name=Bootstrap EPEL
 mirrorlist=http://mirrors.fedoraproject.org/mirrorlist?repo=epel-\$releasever&arch=\$basearch
 failovermethod=priority
 enabled=0
 gpgcheck=0
 EOM</pre>

<pre>yum --enablerepo=epel -y install epel-release
 rm -f /etc/yum.repos.d/epel-bootstrap.repo</pre>

Install rpmforge repo

<pre>rpm --import http://apt.sw.be/RPM-GPG-KEY.dag.txt
 rpm -Uvh http://packages.sw.be/rpmforge-release/rpmforge-release-0.5.2-2.el6.rf.x86_64.rpm
 yum clean all</pre>

Install the virtualbox repo

<pre>yum install -y wget
cd /etc/yum.repos.d
wget http://download.virtualbox.org/virtualbox/rpm/rhel/virtualbox.repo
yum update</pre>

<pre></pre>

Now the interesting bits, lets get to the vbox install.  Although we;ve enabled dkms, I like to also install as if we didn&#8217;t.  It populated the system with the pieces we need in a way that Im used to.  I&#8217;m not a sysadmin by day, so this may be redundant.  YMMV, etc.   First install the Development Tools. There are a lot here, it may take a bit depending on machine specs and connectivity. 

<pre>yum groupinstall "Development Tools"</pre>

<pre></pre>

&nbsp;