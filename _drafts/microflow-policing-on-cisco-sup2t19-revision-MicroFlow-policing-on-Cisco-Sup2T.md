---
id: 218
title: MicroFlow policing on Cisco Sup2T
date: 2012-10-19T01:21:00-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2012/10/19-revision/
permalink: /2012/10/19-revision/
---
Let me save you some time&#8230;.Microflow Policing on the Catalyst 6500 / Sup2TXL doesn&#8217;t yet work. Inbound it &#8220;kinda works&#8221;.  You can configure it and it applies as a service policy, but even though outbound is &#8220;supported in hardware on the Supervisor2TXL&#8221;, there is no software support for it in either the 15.0SY or 12.2(50)SY.  It took me a month to suss this out&#8230;..  
Yes, I should have suspected.  I dont work on Cisco every day, I have Juniper MX, Brocade MLX and a multitude of other platforms to work on daily, so it took a bit.  
The short answer is that the capability won&#8217;t be there until 15.1&#8230;.something I&#8217;m not looking forward to since 15.x is very different, and, if you use any of the MLS features, get ready to re-learn them all.  I still have a strong belief that 15.0SY is missing half of the MLS knobs I need to turn. 

Please, someone correct me.  I&#8217;d be **<u>extremely</u>** happy to be wrong about this one.  

<div>
  [[ This is a content summary only. Visit my website for full links, other content, and more! ]]
</div>