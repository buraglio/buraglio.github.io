---
id: 567
title: A missing link
date: 2013-03-28T21:32:30-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2013/03/564-revision-2/
permalink: /2013/03/564-revision-2/
---
Lately I&#8217;ve been lamenting the fact that there seems to be a lack of options in a very specific product level.  Lets say you have a network that looks like this:

[<img class="alignleft size-full wp-image-565" alt="10G-Bldg" src="http://www.forwardingplane.net/wp-content/uploads/2013/03/10G-Bldg.jpg" width="432" height="599" srcset="http://www.forwardingplane.net/wp-content/uploads/2013/03/10G-Bldg.jpg 432w, http://www.forwardingplane.net/wp-content/uploads/2013/03/10G-Bldg-216x300.jpg 216w" sizes="(max-width: 432px) 100vw, 432px" />](http://www.forwardingplane.net/wp-content/uploads/2013/03/10G-Bldg.jpg)Right Away you&#8217;re limited since you need MPLS and more than 2 10G interfaces, full support for IPv6 and ISIS.

If budget is of any concern, you&#8217;re in trouble.

For many, Cisco pricing and smartnet is potentially going to exclude anything reasonable from them.  There are a substantial amount of non-enterprise folks out there that can&#8217;t afford the Cisco price tag but need the features.  I am here to say, this is a problem.  The attitude of &#8220;if you want the best you have to pay for it

Juniper has the MX80, but it has a carrier grade price tag as well.  Juniper has limited MPLS support on the EX series, but the EX4200, which is arguably the most tried and true, has only 2 ports of 10G and limited MPLS support.  The EX4500 is a tad better with its huge amount of 10G ports, but it has the same limited MPLS support and a crippled ARP and FIB table.

Then you have the Brocade CES/R.  It is close.  The newer version has  4 x 10G ports, MPLS support (with a license), more appropriately priced support and, as a value add, very good OpenFlow support.  It is still limited as far as 10G scalability, so adding more access switches could be problematic.

&nbsp;

&nbsp;