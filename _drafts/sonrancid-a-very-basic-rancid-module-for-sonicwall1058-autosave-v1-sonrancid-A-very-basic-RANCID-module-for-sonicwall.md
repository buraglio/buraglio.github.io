---
id: 1088
title: 'sonrancid: A [very] basic RANCID module for sonicwall'
date: 2014-09-15T07:51:28-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2014/09/1058-autosave-v1/
permalink: /2014/09/1058-autosave-v1/
---
I know, I know, I&#8217;m always saying that you don&#8217;t need a firewall. That&#8217;s mostly to get your attention to push my agenda of sane security architecture, I do actually believe that firewalls are appropriate in a great many use cases and I&#8217;ve managed them big and small ranging from [Juniper SRX 5800 clusters](http://www.forwardingplane.net/2010/08/juniper-srx-cluster/ "Juniper SRX Cluster") to tiny purpose built BSD distros on custom hardware. I even managed <a href="http://www.checkpoint.com/" target="_blank">Checkpoint</a> and <a href="http://www.kulichki.com/moshkow/SECURITY/gauntlet.txt" target="_blank">gauntlet firewall</a> back in the 1990s. And <a href="https://www.novell.com/products/bordermanager/" target="_blank">Novell Border manager</a>&#8230;.good gravy&#8230;.border manager. I just had a chill, that thing is still around.  They work well when spec&#8217;d, designed, maintained correctly and placed in an appropriate location in a network architecture.  That said, I have a few SonicWall devices that I work on occasionally and it has always irritated me that there was not a usable <a href="http://www.shrubbery.net/rancid/" target="_blank">RANCID</a> module for it.  To that end, I hacked up the Cisco RANCID script to support very rudimentary config backups.

_<Insert comment about having some DevOps skills is useful, even if they are very basic like mine.>_

The script will log in and pull the config and version using the following commands:

<pre>show current-config</pre>

<pre>show version</pre>

I am really hoping that someone else will pick it up and massage it a bit because it is very chatty and will produce a diff every time due to the way SonicOS presents some of its configuration parameters. It also needs tested against larger SonicWall devices as I only have smaller boxes to run against.  I know it works against a TZ210, YMMV. Please post comments on github if you use it with anything else.   The password hash is particularly annoying, it always changes when the configuration is displayed. Some of the framework is there to remove it so I may hack at it a bit more but it&#8217;s usable in the loosest sense for the short term.  It&#8217;s available on <a href="https://github.com/buraglio/sonrancid" target="_blank">my github site</a>.