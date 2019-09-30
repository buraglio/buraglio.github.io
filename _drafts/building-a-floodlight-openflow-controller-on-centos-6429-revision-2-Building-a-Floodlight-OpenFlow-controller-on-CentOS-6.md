---
id: 431
title: Building a Floodlight OpenFlow controller on CentOS 6
date: 2013-02-04T11:03:25-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2013/02/429-revision-2/
permalink: /2013/02/429-revision-2/
---
A bit of back history: I came from BSD land. I was a FreeBSD user from way back in the 1990s. BSD land is a land of secure boxes and very high uptimes.  It&#8217;s also a land of arguably clunky package support, a lot of compiling by hand and these days, not nearly as encompassing package and network tuning support.  [I decided to move to Linux](http://www.forwardingplane.net/2011/06/better-support-for-linux-and-annoyed-about-it/ "Better support for Linux (and annoyed about it)") a while ago, reluctantly, and chose Debian as my flavor of choice.  I do love debian, however, I very quiuckly realized that even debian is a bit of a fringe OS build of Linux.  Commercial support is nearly all based on RHEL.  Folks that run RHEL also run CentOS.  We run both in my day job.  About a year ago to   I, once again, decided  I needed to learn CentOS.

There are a lot of posts about building floodlight as an openflow controller.  I used this tutorial <a href="http://networkstatic.net/floodlight-openflow-controller-gui-applet/" target="_blank">Brent Salisbury did</a> to build mine. There is a good one on the <a href="http://floodlight.openflowhub.org/getting-started/" target="_blank">openflow hub</a> site as well.  I&#8217;ve found that many are based on Debian or Ubuntu, which can be subtly different than a CentOS / RHEL experience.

&nbsp;

In CentOS, log in and sudo -s or su to root.  Install the prereqs:

_yum -y install build-essential default-jdk ant python-dev eclipse git_  
_mkdir /services/floodlight_  
_cd /services/floodlight/_  
_git clone git://github.com/floodlight/floodlight.git  
ant_

Start floodlight in the background.  
_./floodlight.sh &_

Because I&#8217;m terrible at looking at directions, I went to the base URL. This will yield an error that looks something like this:

<pre>{"name":"Not Found","error":true,"throwable":null,"description":"The server has not found anything matching the request URI","success":false,"informational":false,"code":404,"reasonPhrase":"Not Found","uri":"http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.5","serverError":false,"connectorError":false,"clientError":true,"globalError":false,"redirection":false,"recoverableError":false}</pre>

The right way to access floodlight is to use the entire URL:

http://<address>:8080/ui/index.html

Learn from my stupidity.

&nbsp;

Here is a script to build it for you:

<pre>#!/bin/bash

echo "Installing prerequisits:"
yum -y install build-essential default-jdk ant python-dev eclipse git

echo "Installing floodlight to /services/floodight/"
mkdir /services/floodlight
cd /services/floodlight/
git clone git://github.com/floodlight/floodlight.git
ant

echo "Starting floodlight:"

./floodlight.sh&
echo "Floodlight started, point your beowser at http://&lt;address&gt;:8080/ui/index.html"
</pre>

&nbsp;

&nbsp;

&nbsp;