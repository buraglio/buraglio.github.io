---
id: 82
title: Converting (back) to wordpress from Blogger
date: 2012-12-02T13:18:03-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2012/12/77-revision-5/
permalink: /2012/12/77-revision-5/
---
For a long time I ran a blog called [tech.buraglio.com](http://www.forwardingplane.net) that was a self hosted wordpress site. After having kids and getting a bit busier at work, I decided to move everything that I had been hosting (images, scripts, hacks, blogs and DNS) to &#8220;the cloud&#8221;. I managed to do this for everything but my primary DNS resolver, which I had always intended to keep, and one [wordpress blog](http://www.shitenonions.com) that I hosted for someone else.

I moved my image hosting from gallery2 to flickr (backup on picasaweb), secondary DNS to nether.net and afraid.org, scripts, hacks and the like to google code and my blogs to blogger.  Blogger was **very** easy, stable and highly available.  It was also far less flexible.

<p style="text-align: center;">
  <img class="aligncenter" src="http://www.undertheradarblog.com/wp-content/uploads/2011/12/Top-5-Best-Free-Cloud-Storage-Services-That-You-Need-And-Are-Useful.png" alt="" width="480" height="253" />
</p>

I continued to write from time to time, mostly ramblings or notes on some weird thing I has to set up.  I noticed that a few of my posts were getting a decent amount of traffic, something I was a bit surprised about.  I started to write a bit more&#8230;&#8230;more traffic.  I started cross posting to <a href="http://www.twitter.com/buraglio" target="_blank">twitter</a>.  More traffic.  OK, maybe what I was jotting down was actually useful to someone.  Or I had a stalker.  Probably not the latter.

Since I already had apache working and serving other stuff, and one of them is another WP site, I already has MySQL running.  I just enabled SSL for the new domain that I had added and was ready to go.  I&#8217;m a really lazy sysadmin, so I used this as a reference.

First, installing wordpress.  I chose the <a href="http://codex.wordpress.org/Installing/Updating_WordPress_with_Subversion" target="_blank">SVN install</a> for easier upgrades down the road.  Upgrading WP was somethingI alweays hated doing, so I let it languish when I used it before.  At least now I should, in most cases, be able to just type &#8220;_svn update_&#8221; to get it up to date (after verifying a back up, of course).

OK, so this should be pretty straight forward, right?  Maybe not.  I&#8217;ve done a lot of twitter and bit.ly linking to my posts and I had a feedburner and quite a few RSS subscribers.  The feedburner stuff I&#8217;m probably going to have to write off.  The <a href="http://feeds.feedburner.com/forwardingplane/WszR" target="_blank">link</a> needed to be more obvious as to what it was. The biggest thing I have to worry about is that Blogger formats it&#8217;s &#8220;pretty&#8221; links in a different way than wordpress.  Thankfully, however, I&#8217;m self gosting so I can use apache magic to fix this.

.htaccess to the rescue.

After using the <a href="http://wordpress.org/extend/plugins/blogger-importer/" target="_blank">blogger importer</a>, I had to go through and set all of my old blogger drafts to draft status again, wordpress has changed them all to published status.