---
id: 569
title: A missing link
date: 2013-03-28T22:38:20-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2013/03/564-revision-3/
permalink: /2013/03/564-revision-3/
---
Lately I&#8217;ve been lamenting the fact that there seems to be a lack of options in a very specific product level.  Lets say you have a network that looks like this:

&nbsp;

[<img class="alignleft size-full wp-image-568" alt="10G-Bldg" src="http://www.forwardingplane.net/wp-content/uploads/2013/03/10G-Bldg1.jpg" width="432" height="599" srcset="http://www.forwardingplane.net/wp-content/uploads/2013/03/10G-Bldg1.jpg 432w, http://www.forwardingplane.net/wp-content/uploads/2013/03/10G-Bldg1-216x300.jpg 216w" sizes="(max-width: 432px) 100vw, 432px" />](http://www.forwardingplane.net/wp-content/uploads/2013/03/10G-Bldg1.jpg)Right Away you&#8217;re limited since you need MPLS and more than 2 10G interfaces, full support for IPv6 and ISIS.

If budget is of any concern, you&#8217;re in trouble.

For many, Cisco pricing and smartnet is potentially going to exclude anything reasonable from them.  There are a substantial amount of non-enterprise folks out there that can&#8217;t afford the Cisco price tag but need the features.  I am here to say, this is a problem.  The attitude of &#8220;if you want the best you have to pay for it&#8221; doesn&#8217;t apply.  There is a need for viable alternatives.

Juniper has the MX80, but it has a carrier grade price tag as well.  Juniper has limited MPLS support on the EX series, but the EX4200, which is arguably the most tried and true, has only 2 ports of 10G and limited MPLS support.  The EX4500 is a tad better with its huge amount of 10G ports, but it has the same limited MPLS support and a crippled ARP and FIB table.

Then you have the Brocade CES/R.  It is close.  The newer version has  4 x 10G ports, MPLS support (with a license), more appropriately priced support and, as a value add, very good OpenFlow support.  It is still limited as far as 10G scalability, so adding more access switches could be problematic.

HP has some great products in the Procurve series.  They&#8217;re inexpensive, rock solid and packed with features. Unfortunately, the ones that meet the port density are fairly good sized chassis and none of them have MPLS.  Now, they do have an intriguing line up in the H3C series.  I believe there may be an option there, however, I have no idea on pricing and have yet to see one actually do MPLS (although they claim support).  I&#8217;m cautiously optimistic.

Then you have Alcatel Lucent.   They do MPLS, they&#8217;re carrier devices.  They offer a 1U (  
(<a href="http://www.alcatel-lucent.com/products/7210-service-access-switch" target="_blank">7210 Service Access Switch</a>) device but I have no idea on cost and I&#8217;m still looking for 10G port density.  I suspect it is very reasonable.  Their CLI is a bit different but they&#8217;re very robust devices.  I&#8217;ve not used any but the 7750, so I cant comment as to how the smaller ones look.  It&#8217;s a possibility if it has the 10G ports.

Arista is very close but they fall short on the MPLS support.

&nbsp;

The primary take away from this commentary is that there are not a lot of options that meet the following criteria:

  * 1-2U
  * > 4 10G ports
  * MPLS
  * Dual power supplies
  * > 16,000/4,000 IPv4/IPv6 routes
  * IPv6 support
  * ISIS
  * 40G uplink
  * OpenFlow support or roadmap
  * **Reasonably priced**

I keep coming back to the old adage of &#8220;Cheap, Fast, Reliable.  Pick Two&#8221; and it drives me crazy.  We should have more options but I don&#8217;t think we do.  I would absolutely **love** to be wrong, but every time I look at this I feel like I am picking out a cell phone plan.  The affordable ones are never quite enough and the plan above is overkill and too expensive.

&nbsp;