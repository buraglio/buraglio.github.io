---
id: 1315
title: Solarwinds Orion from a UNIX user point of view
date: 2015-07-06T22:08:30-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2015/07/1292-revision-v1/
permalink: /2015/07/1292-revision-v1/
---
Back in February of this year (2015) I was introduced to [Solarwinds](http://www.solarwinds.com/) when they presented to us at [Networking Field day 9](http://techfieldday.com/event/nfd9/). Until then I knew of SolarWinds products but only at a cursory level; I had never really seen or used their stuff since it was mostly focused on environments that were either smaller or outside of the networking world that I generally operate in. However, I am a[n insufferable] network monitoring &#8220;aficionado&#8221; so when the opportunity to play around with it arose, I happily took it.  
Now, let me preface what comes next by laying out a few things:

  1. I am not a fan of SNMP. In fact, I hate it. It&#8217;s the least intuitive, overly complex protocol used for management that we can&#8217;t get away from. It sucks and is CPU intensive. It is cryptic, dated and we&#8217;ve tried to fix it by bolting on crude, poorly supported security features.
  2. I don&#8217;t do windows systems. I have not managed as much as a windows desktop other than an on-demand VM for the occasional DWDM network element manager since 1999. I have no issue with it as a platform but a unix based platform is a better tool for my every day workflow (see [NIX4NetEng](https://www.forwardingplane.net/topics/nix4neteng/))  so I don&#8217;t have it in my wheelhouse and have no business managing such a system.
  3. I went into this project completely and totally open minded. These were the canvas, brushes and subject I had to work with and it needed to do what needed done.

With that out of the way, my impressions of SolarWinds Orion platform at first glance were: &#8220;Wow, this is pretty good&#8221;.<img class="alignright size-full wp-image-1313" src="http://www.forwardingplane.net/wp-content/uploads/2015/07/Screen-Shot-2015-07-06-at-10.48.05-PM.png" alt="Screen Shot 2015-07-06 at 10.48.05 PM" width="256" height="205" />

I must admit, I was surprised. Although I went in open minded, I knew that Orion is a tool that seemed to be enterprise focused, which was not the application it was being used for. It runs on windows systems, it had &#8220;rumored&#8221; scaling issues in large environments, and they market it mostly to the enterprise demographic, at least from my point of view. Admittedly I struggled with the configuration. I&#8217;m a little old school and I like to kick the tires of a GUI and then to most of the heavy lifting in a conf file or set of files using VI, which I was not able to do here. I found the management a little clunky and sluggish at times, but the data presentation was top shelf and once I figured out the where and how I was able to set up netflow, syslog collection and up/down monitoring in pretty short order. In this environment I didn&#8217;t yet have IPv6 so no sflow or IPFIX in the mix yet; not sure about IPv6 support in practice.

A rough breakdown of the pros and cons from my inaugural run:

**Pros:**

  * Elegant Interface
  * Eye candy
  * One stop shop\***
  * Good support for common stuff, seems expandable.
  * Great [community of support](https://thwack.solarwinds.com); very &#8220;FOSS-Like&#8221;
  * Lots of knobs and dials for tuning.
  * Did I say good interface?
  * Automated netflow database maintenance is cool.
  * Search for flows and syslogs is reasonably fast. &#8211; a litmus test for real use.

**Cons:**

  * It&#8217;s SNMP. We&#8217;re mostly stuck with that, unfortunately.
  * Interface configuration took a little getting used to coming from a CLI background (this is a &#8220;me problem&#8221;)
  * Cost; it&#8217;s a reasonably noticeable capital expenditure.

**Unknowns: **

  * I didn&#8217;t get to play with the SNMP trap management.
  * I kept RANCID for configurations management.

The key for this for me was that I did not need to manage the server. I had no access whatsoever to the underlying OS, meaning the responsibility of managing this host OS was completely off the table. I was able to manage the SolarWinds instance from its web interface without issue.

[<img class="alignright  wp-image-1310" src="http://www.forwardingplane.net/wp-content/uploads/2015/07/Screen-Shot-2015-07-06-at-10.47.36-PM.png" alt="Screen Shot 2015-07-06 at 10.47.36 PM" width="354" height="340" />](http://www.forwardingplane.net/wp-content/uploads/2015/07/Screen-Shot-2015-07-06-at-10.47.36-PM.png)

My summary: If you are comfortable in a windows environment or do not manage the underlying system, don&#8217;t need granular flow and syslog analysis for forensics and have the cash, it&#8217;s a full featured, supported platform. I continue to learn more and more about the seemingly endless stuff this platform can do. If you are strapped for cash and/or are comfortable going the FOSS route, you have a lot of options at the expense of configuration time and possible learning curve.

You&#8217;ll spend the money wither way, either on people time or on licensing. In some cases possibly both.

** I&#8217;ve heard that as a rumor. In my experience with the devices and other network elements it managed it seemed to work pretty well and I had no scaling issues.

\*** Depends heavily on needs and requirements.