---
id: 468
title: CentOS KVM Install
date: 2013-03-01T12:57:25-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2013/03/467-revision/
permalink: /2013/03/467-revision/
---
I&#8217;ve been a virtualization user forever, VMware, VirtualBox, Parallels, whatever.  I&#8217;d not really messed around much with qemu or KVM, but some projects I was working on suggested it for the virtualization mechanism, so I figured I&#8217;d learn it.  Heck, I think the hosting provider  of this blog is using it to provide the VPS that this site runs on.

A few things became obvious pretty quickly:

It&#8217;s very robust.

It&#8217;s got a lot of documentation, but not all of it is straightforward.

It has a lot of pieces needed to make it work efficiently.

Here is what I had to do to get it running on a fresh install of CentOS 6.3.

Install all the dependancies.  And there were many.  Coming from using the VirtualBox CLI, little things that I expected didn&#8217;t work if I didn&#8217;t have this or that installed.

<!--?xml version="1.0" encoding="UTF-8" standalone="no"?-->

_<span style="font-family: Verdana;">yum install -y qemu-kvm.x86_64 qemu-kvm-tools.x86_64 </span>kvm libvirt bridge-utils tunctl python-virtinst.noarch avahi _

&nbsp;