---
id: 392
title: Diff RANCID router configs with SVN
date: 2013-01-24T13:33:11-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2013/01/389-revision-3/
permalink: /2013/01/389-revision-3/
---
If you are running a network and aren&#8217;t using <a href="http://shrubbery.net/rancid/" target="_blank">RANCID</a>, you should give it a serious look.  RANCID is a cross platform configuration management toolkit for backing up router configurations and certain environmental and hardware information into version control.  It&#8217;s been around for as long as I can remember and supports nearly every platform I can think of, including a <a title="VDXrancid contrib scripts" href="http://www.forwardingplane.net/2012/11/vdxrancid-contrib-scripts/" target="_blank">few</a> <a title="alurancid and pfrancid" href="http://www.forwardingplane.net/2011/06/alurancid-and-pfrancid/" target="_blank">modules</a> that I cobbled together myself.  There is are a few nice web based front ends for CVS and SVN, I prefer to use <a href="http://www.viewvc.org" target="_blank">ViewVC</a> because I have a lot of experience with it, however, there may be cases where a web server isn&#8217;t a good option, unavailable or just too much work.  In this case, you&#8217;ll want to know how to diff those configs from the CLI using the existing tools.  I find myself always forgetting the exact syntax of how to do this, so here it is. I prefer to use SVN, so we&#8217;ll talk about that one here.

&nbsp;

svn list will give a list of current devices in version control:

<pre>svn list</pre>

<pre>rtr1.company.com
rtr2.company.com
rtr3.company.com
sw1.company.com
sw2.company.com</pre>

To look at a router config:

<pre>svn cat &lt;router&gt;
svn cat rtr1.company.com</pre>

See all revisions:

<pre>svn log &lt;router&gt;</pre>

<pre>svn log rtr1.company.com</pre>

<pre>------------------------------------------------------------------------
r863 | _rancid | 2013-01-18 12:51:59 -0600 (Fri, 18 Jan 2013) | 1 line
updates - Change made by: buraglio
------------------------------------------------------------------------
r848 | _rancid | 2013-01-09 14:00:27 -0600 (Wed, 09 Jan 2013) | 1 line
updates
------------------------------------------------------------------------
r847 | _rancid | 2013-01-09 02:07:42 -0600 (Wed, 09 Jan 2013) | 1 line
updates
------------------------------------------------------------------------
r832 | _rancid | 2012-12-12 09:42:33 -0600 (Wed, 12 Dec 2012) | 1 line</pre>

<pre>updates - Change made by: buraglio
------------------------------------------------------------------------
r804 | _rancid | 2012-11-27 14:00:28 -0600 (Tue, 27 Nov 2012) | 1 line</pre>

updates

<pre></pre>

Diff revisions:

<pre>svn diff -r &lt;version1&gt;:&lt;version2&gt; &lt;router&gt;
svn diff -r r863:r847 rtr1.company.com</pre>