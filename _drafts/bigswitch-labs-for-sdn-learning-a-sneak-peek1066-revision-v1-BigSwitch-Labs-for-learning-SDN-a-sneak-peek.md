---
id: 1092
title: BigSwitch Labs for learning SDN, a sneak peek!
date: 2014-09-15T15:05:56-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2014/09/1066-revision-v1/
permalink: /2014/09/1066-revision-v1/
---
I was recently granted access to the beta <a href="http://www.bigswitch.com/" target="_blank">BigSwitch Networks</a> lab site, a purpose built classroom in the cloud focused on teaching the BigSwitch SDN environment.  I had seen some of the BSN offerings in the past and always held them in high regard, but I was thoroughly impressed with both the completeness of the lab and how polished the controller environment was.<img class="aligncenter wp-image-1070" src="http://www.forwardingplane.net/wp-content/uploads/2014/09/Screenshot-2014-09-12-10.28.50.png" alt="Screenshot 2014-09-12 10.28.50" width="500" height="308" />  At the time of this writing, the lab consists of 3 modules: Building cloud fabric, monitoring fabric and dynamic provisioning of monitoring fabric.  For the scope of this post, I&#8217;ll concentrate on the first, building cloud fabric.  I&#8217;m a big fan of the CLI [yes, I know SDN is supposed to &#8220;kill the CLI&#8221;. Whatever.  I don&#8217;t by the sensationalism], and one thing that jumped right out to me was that they provide the GUI and the CLI, and that the CLI is familiar to anyone that has worked on an IOS device.  The lab is useful, even for someone that has done some SDN, both on production or in a lab, in that it presents the fundamentals in a way that both demonstrates the purpose and function and lays out the technology and product.

From the technology presentation standpoint, the BigSwitch offering is quite impressive.

The reality of it is that, in my experience, GUIs don&#8217;t always have the most intuitive or complete implementations and they&#8217;re hard to automate.  Now, from what I&#8217;ve seen to far the bigswitch offing is the exception to that rule.  <img class="aligncenter wp-image-1084" src="http://www.forwardingplane.net/wp-content/uploads/2014/09/Screenshot-2014-09-12-10.50.19.png" alt="Screenshot 2014-09-12 10.50.19" width="500" height="307" />

Nevertheless, part of my usual workflow is to use one to define the other.  What I mean by that is that if I don&#8217;t know exactly how to accomplish my goal in the GUI, I switch to the CLI and see what I can do from there, returning to the GUI to see what has changed and then reverse engineer it from that perspective.  The opposite is also true, I have used the CLI to define the GUI _:cough:_ <a href="http://www.juniper.net/us/en/products-services/security/netscreen/" target="_blank">netscreen</a> _:cough:_.

I am particularly big fan of the &#8220;debug rest&#8221; option in the CLI, allowing the commands sent to automatically pop up with the rest interface commands necessary to utilize them.

&nbsp;

In the time I&#8217;ve spent within this system,