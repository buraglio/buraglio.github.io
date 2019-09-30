---
id: 629
title: Scripting the build of OpenDayight Controller under CentOS
date: 2013-05-03T12:28:35-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2013/05/627-revision-2/
permalink: /2013/05/627-revision-2/
---
<a href="https://twitter.com/blinken_lichten" target="_blank">Jon Langemak</a> has a great write up on <a href="http://www.dasblinkenlichten.com/installing-opendaylight-on-centos/" target="_blank">building the OpenDaylight controller under CentOS</a>. Since I&#8217;ll have to do this a bunch of times, I though tI&#8217;d take what he so generously put online and build a very rudimentary script for deploying ODC under CentOS. The prerequisites are that you already have an account and ssh key at the <a href="https://git.opendaylight.org/" target="_blank">OpenDaylight GIT repo</a>. 

Here is the script: