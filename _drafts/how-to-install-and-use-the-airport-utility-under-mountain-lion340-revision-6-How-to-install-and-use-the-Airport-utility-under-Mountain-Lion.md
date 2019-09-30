---
id: 349
title: How to install and use the Airport utility under Mountain Lion
date: 2013-01-08T23:47:46-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2013/01/340-revision-6/
permalink: /2013/01/340-revision-6/
---
I have a bunch of Apple wireless gear  at my house.  It&#8217;s inexpensive, feature rich and easy to maintain.  However, with the update to mountain lion a while ago, the ability to install  the older Airport Utility stopped.  This is annoying since I have what apple now considers &#8220;advanced&#8221; features like IPv6 at my home and essentially all my gear here is a lab (except for the plex server =)

I&#8217;ve been spending a lot of time on <a href="http://www.cacti.net" target="_blank">cacti</a> lately, and I wanted to test out the syslog plugin&#8230;.ok, easy.  It&#8217;s all set up.  Then I got to thinking &#8220;why not just let this run and syslog all my gear like the good &#8216;ol days?&#8221;  Nerdy?  Yes, but hey, I collect flow data at home and have a <a href="http://www.forwardingplane.net/homenet/" target="_blank">weathermap</a> of my home network.  It keeps me eating my own dog food with the netflow exporter plugin on <a href="http://www.pfsense.org" target="_blank">pfSense</a> and it&#8217;s fun.

Uh, oh.  No ability to set syslog receiver on the airport gear anymore.  Not cool.  [Guess what, no way to change IPv6 settings anymore either]

No way to do a standard install of the old utility. Lame, Apple, Lame.  After poking around a bit I found a pretty easy way to do it as long as you&#8217;re not afraid of the command line.

Since at least a few other folks will want to do this, here it is:

<a href="http://support.apple.com/kb/DL1536" target="_blank">Download the App</a> from Apple.

Mount the Downloaded disk.

Open Terminal.

Type:

<pre>pkgutil --expand /Volumes/AirPortUtility/AirPortUtility56.pkg
cd ~/Desktop/AirPortTemp~/Desktop/AirPortTemp/AirPortUtility56Lion.pkg/
open Payload
cd "Payload 2 2/Applications/Utilities/"
open .</pre>

[<img class="aligncenter size-full wp-image-341" title="Screen Shot 2013-01-08 at 11.32.08 PM" src="http://www.forwardingplane.net/wp-content/uploads/2013/01/Screen-Shot-2013-01-08-at-11.32.08-PM.png" alt="" width="417" height="370" srcset="http://www.forwardingplane.net/wp-content/uploads/2013/01/Screen-Shot-2013-01-08-at-11.32.08-PM.png 417w, http://www.forwardingplane.net/wp-content/uploads/2013/01/Screen-Shot-2013-01-08-at-11.32.08-PM-300x266.png 300w" sizes="(max-width: 417px) 100vw, 417px" />](http://www.forwardingplane.net/wp-content/uploads/2013/01/Screen-Shot-2013-01-08-at-11.32.08-PM.png)

Done.  That should open a finder window with the App in it.  You can copy it to you /Applications/Utilities folder and use it alongside the newer one.  You&#8217;ll need to authenticate to copy into the /Applications/Utilities directory.

Edits made and Poof!  Now I can see my syslogs:

<p style="text-align: center;">
   <a href="http://www.forwardingplane.net/wp-content/uploads/2013/01/Screen-Shot-2013-01-08-at-11.44.40-PM.png"><img class="aligncenter  wp-image-347" title="Screen Shot 2013-01-08 at 11.44.40 PM" src="http://www.forwardingplane.net/wp-content/uploads/2013/01/Screen-Shot-2013-01-08-at-11.44.40-PM-1024x349.png" alt="" width="614" height="209" srcset="http://www.forwardingplane.net/wp-content/uploads/2013/01/Screen-Shot-2013-01-08-at-11.44.40-PM-1024x349.png 1024w, http://www.forwardingplane.net/wp-content/uploads/2013/01/Screen-Shot-2013-01-08-at-11.44.40-PM-300x102.png 300w, http://www.forwardingplane.net/wp-content/uploads/2013/01/Screen-Shot-2013-01-08-at-11.44.40-PM-550x187.png 550w, http://www.forwardingplane.net/wp-content/uploads/2013/01/Screen-Shot-2013-01-08-at-11.44.40-PM.png 1516w" sizes="(max-width: 614px) 100vw, 614px" /></a>
</p>

&nbsp;