---
id: 129
title: 'Sonicwall &#8211; Old dog learns new tricks'
date: 2012-12-07T16:42:50-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2012/12/107-revision-13/
permalink: /2012/12/107-revision-13/
---
~12 years ago I had a drinking buddy that worked with me at the regional ISP.   We had a lot in common, he had been an icon back in the [didjits](http://en.wikipedia.org/wiki/The_Didjits) era of punk rock in Champaign Urbana and we had briefly been in a terrible band together.  He introduced me to a dude that to this day I just knew as &#8220;Ravi Sonicwall&#8221;.  He had apparently been recruited from the U of I, written a lot of the low level pieces of the original sonicwall and retired to enjoy life and buy beers (he actually scolded me at a bar for buying him a beer saying &#8220;when I&#8217;m in town, I buy the beers&#8221;).

I had purchased a few sonicwall boxes after that, having only really used linux, IOS, checkpoint on nokia boxes and *_shudder_* Novell Border manager.  I liked the boxes since they had a GUI and I could hand off day-to-day operations to someone that !=Me.  After a year or so in production, I started to become frustrated with them,  the ones I had lacked a CLI completely and had fallen behind on the things I needed to do with them.   Their cost to feature wasn&#8217;t there for what I needed and the ones I had purchased systematically had hardware failures all within 7 months.  I wrote off sonicwall completely at that point.

Fast forward a decade.

Sonicwall purchased by Dell.

We&#8217;ve heavily invested in the Juniper SRX.

The SRX does what we ask of it.

The SRX has some limitation as far as management and display of eye candy.

While I personally like a CLI to rummage around in, not everyone does.  Palo Alto Networks has an amazing GUI.  Like, the best I&#8217;ve ever seen.  Sonicwall&#8230;&#8230;well, theirs always left me wanting back in the day.  Now&#8230;..wow, a totally different ballgame.

Don&#8217;t get me wrong, the Soniceall &#8220;Super Massive&#8221; still can&#8217;t compete (in this guys opinion) with a Juniper 5800.  **However, **their transparent mode is a tad better and their web management is an order of magnitude better.  Performance?  I don&#8217;t think anything can touch an SRX loaded with SPCs.

That being said, I have the Sonicwall we had as a demo a good go around.  I found it&#8217;s ease of setup pretty refreshing.  For those that have non-networking savvy security folks running these boxes, they&#8217;ll likely love the interface.  I like the AppFlow Monitor.  It&#8217;s a nice reprensentation of the transit data in an easy to understand format.  Here is an example of the box in my lab after running a few days.

[<img class="alignnone  wp-image-116" title="SonicWall AppFlow Monitor " src="http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.09.41-PM-1024x256.png" alt="" width="491" height="123" srcset="http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.09.41-PM-1024x256.png 1024w, http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.09.41-PM-300x75.png 300w, http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.09.41-PM-550x137.png 550w, http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.09.41-PM.png 1176w" sizes="(max-width: 491px) 100vw, 491px" />](http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.09.41-PM.png) [  
](http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.09.41-PM.png) 

&nbsp;

The threat reports are nice as well, very eye candy and they seem pretty accurate based on what we threw at it and what we generally see in the wild west.

&nbsp;

[<img class="wp-image-120 alignleft" title="Screen Shot 2012-12-07 at 4.09.48 PM" src="http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.09.48-PM-1024x256.png" alt="" width="491" height="123" srcset="http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.09.48-PM-1024x256.png 1024w, http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.09.48-PM-300x75.png 300w, http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.09.48-PM-550x137.png 550w, http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.09.48-PM.png 1178w" sizes="(max-width: 491px) 100vw, 491px" />](http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.09.48-PM.png)

[<img class="wp-image-123 alignleft" title="Screen Shot 2012-12-07 at 4.09.41 PM" src="http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.09.41-PM1-1024x256.png" alt="" width="491" height="123" srcset="http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.09.41-PM1-1024x256.png 1024w, http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.09.41-PM1-300x75.png 300w, http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.09.41-PM1-550x137.png 550w, http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.09.41-PM1.png 1176w" sizes="(max-width: 491px) 100vw, 491px" />](http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.09.41-PM1.png)

[<img class="wp-image-121 alignleft" title="Screen Shot 2012-12-07 at 4.10.00 PM" src="http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.10.00-PM-1024x256.png" alt="" width="491" height="123" srcset="http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.10.00-PM-1024x256.png 1024w, http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.10.00-PM-300x75.png 300w, http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.10.00-PM-550x137.png 550w, http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.10.00-PM.png 1173w" sizes="(max-width: 491px) 100vw, 491px" />](http://www.forwardingplane.net/wp-content/uploads/2012/12/Screen-Shot-2012-12-07-at-4.10.00-PM.png)

&nbsp;

&nbsp;