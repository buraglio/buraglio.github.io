---
id: 390
title: Diff RANCID router configs with SVN
date: 2013-01-23T08:22:16-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2013/01/389-revision/
permalink: /2013/01/389-revision/
---
If you are running a network and aren&#8217;t using <a href="http://shrubbery.net/rancid/" target="_blank">RANCID</a>, you should give it a serious look.  RANCID is a cross platform configuration management toolkit for backing up router configurations and certain environmental and hardware information into version control.  It&#8217;s been around for as long as I can remember and supports nearly every platform I can think of, including a <a title="VDXrancid contrib scripts" href="http://www.forwardingplane.net/2012/11/vdxrancid-contrib-scripts/" target="_blank">few</a> <a title="alurancid and pfrancid" href="http://www.forwardingplane.net/2011/06/alurancid-and-pfrancid/" target="_blank">modules</a> that I cobbled together myself.  There is are a few nice web based front ends for CVS and SVN, I prefer to use <a href="http://www.viewvc.org" target="_blank">ViewVC</a> because I have a lot of experience with it, however, there may be cases where a web server isn&#8217;t a good option, unavailable or just too much work.  In this case, you&#8217;ll want to know how to diff those configs from the CLI using the existing tools.

I prefer to use SVN, so we&#8217;ll talk about that one here.

&nbsp;