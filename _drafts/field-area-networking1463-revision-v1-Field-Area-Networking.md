---
id: 1465
title: Field Area Networking
date: 2018-05-04T07:38:15-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2018/05/1463-revision-v1/
permalink: /2018/05/1463-revision-v1/
---
It&#8217;s no secret that RF technologies and what like to call &#8220;specialty networking&#8221; are two of my favorite things in the networking space. **Put them together and it is like chocolate and peanut butter!** Now, some may not consider Field Area Networking (FAN) to be &#8220;unconventional&#8221;, but it certainly falls well outside of the space of what is typically traditional enterprise networking. That said, Cisco&#8217;s FAN briefing at [Network Field Day 17](http://techfieldday.com/event/nfd17/) really got me excited and thinking about the alternatives for the IoT space. Other than cellular LTE or [LTE-M](https://www.link-labs.com/blog/what-is-lte-m), there are few options for remote IoT devices with limited power draw and bandwidth requirements. So I went down the twisted path of investigating that space, and recently, I recorded a [Network Collective](https://thenetworkcollective.com/) short take on the subject, available below.



The NFD 17 Cisco FAN briefing that this is based around is also worth a watch &#8211; this is really innovative stuff that many of us probably don&#8217;t think about.



[Cisco Innovations for the Field Area Network with Rupak Chandra](https://vimeo.com/253197120) from [Stephen Foskett](https://vimeo.com/sfoskett) on [Vimeo](https://vimeo.com).

&nbsp;

### Nick&#8217;s take:

As we talk about things like cloud migration, automation, orchestration, and security architectures, lets consider the sheer scale of not just IoT networking but the sensor and other industrial networking _**outside** _of the enterprise space. The sheer number of devices to be managed in these spaces is stupefying, and the transport of the data created by these networks as well as the management of the devices and network elements is a non-trivial detail. Building out networks such as a sensor network has a completely different scope and scale than a stereotypical enterprise or even a carrier service provider network. Keeping in mind just the number of hosts things like addressing schema become a critical part of the architecture (spoiler: you&#8217;re probably not going to be able to scale IPv4). Power and environmental considerations are also not nearly as squishy as they can be in a nice, controlled data center. Considering those data points, it&#8217;s pretty clear that there is plenty of interesting stuff happening in both the engineering and security areas.

&nbsp;