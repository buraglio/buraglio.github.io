---
id: 733
title: Building a secured network in a box
date: 2013-07-21T11:27:53-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2013/07/731-revision/
permalink: /2013/07/731-revision/
---
In many environments, the move to virtualization is a path well traveled.  My home and lab networks are no exception to this.  I have played with nearly all of the virtualization platforms and am firmly in teh camp that there will be a large segment of networking that will move to a virtualized platform, especially in the data center and campus segments.  Virtualization of routing tables has existed for a long time, see VRF-Lite  and MPLS VRF as well as multi-tenancy technologies like Junipers logical systems.

&#8220;How is a small to medium sized environment going to take advantage of this and more interestingly, how can it be secured?&#8221;

[<img class="alignleft  wp-image-732" alt="Red_onions" src="http://www.forwardingplane.net/wp-content/uploads/2013/07/Red_onions-1024x763.jpg" width="368" height="275" srcset="http://www.forwardingplane.net/wp-content/uploads/2013/07/Red_onions-1024x763.jpg 1024w, http://www.forwardingplane.net/wp-content/uploads/2013/07/Red_onions-300x223.jpg 300w, http://www.forwardingplane.net/wp-content/uploads/2013/07/Red_onions-550x410.jpg 550w, http://www.forwardingplane.net/wp-content/uploads/2013/07/Red_onions.jpg 1600w" sizes="(max-width: 368px) 100vw, 368px" />](http://www.forwardingplane.net/wp-content/uploads/2013/07/Red_onions.jpg)This is a question I inadvertently found at least one answer to when building out my own network and testing a great little project called <a href="http://securityonion.blogspot.com/" target="_blank">security onion</a>.  Now I&#8217;d seen and used this platform a bit in the past, but it had been at least a version ago and my exposure was pretty short.

security onion, VMWare &#8220;Span&#8221; port