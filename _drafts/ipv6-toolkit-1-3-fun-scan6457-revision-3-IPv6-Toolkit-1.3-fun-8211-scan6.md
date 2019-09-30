---
id: 460
title: 'IPv6 Toolkit 1.3 fun &#8211; scan6'
date: 2013-02-19T22:30:53-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2013/02/457-revision-3/
permalink: /2013/02/457-revision-3/
---
Recently <a href="http://www.si6networks.com/tools/ipv6toolkit/" target="_blank">SI6 released the IPv6 Toolkit 1.3 </a>  This release is on the heels of this <a href="http://tools.ietf.org/html/draft-ietf-opsec-ipv6-host-scanning-00" target="_blank">IETF draft </a> on IPv6 host scanning.  It was long thought that scanning an IPv6 network was impossible.  The address space was too large and reliably ascertaining the hosts from it would be too time consuming to even attempt.  However, as <a href="http://en.wikipedia.org/wiki/Hans_Zarkov" target="_blank">Dr. Hans Zarkov </a>says in the 1980 classic cult film of my youth, <a href="http://en.wikipedia.org/wiki/Flash_Gordon_(film)" target="_blank">Flash Gordon</a>, &#8220;You can&#8217;t beat the human spirit!&#8221;  That fine community out there has thought outside the box and found a way.

<img class="alignnone" alt="" src="http://www.thiel-a-vision.com/wp-content/uploads/2010/07/flash68sm.jpg" width="600" height="258" /> 

I&#8217;m a network engineer by profession, but I&#8217;ve been a security guy more than once during my ~15 years doing IT work; I think there is definite value in studying &#8220;the dark side&#8221; and learning it&#8217;s power.  Couple that with my zealotry of IPv6&#8230;.and I&#8217;ve found a time vortex.

Scanning IPv6 is not like scanning IPv4.   It can&#8217;t be.  A /64 network has 18,446,744,073,709,551,616 (18 quintillion) unique addresses and a /64 is the default allocation for an end user subnet.  Have fun scanning that one by one.  The methodology used by scan6 is pretty innovative, but first you have to build it.

The <a href="http://www.si6networks.com/tools/ipv6toolkit/" target="_blank">IPv6 toolkit</a> is available via download <a href="http://www.si6networks.com/tools/ipv6toolkit/ipv6-toolkit-v1.3.1.tar.gz" target="_blank">here</a>.  It is current;y supported under FreeBSD, NetBSD, OpenBSD, Linux, and Mac OS X.  I&#8217;ve chosen to build mine on my laptop, a macbook pro running OS 10.8.

It&#8217;s pretty straightforward to build assuming you have the Developers Tools and CLI support added.

_(~/Downloads/ipv6-toolkit-v1.3) Tardis $ make_  
_gcc -Wall -o flow6 tools/flow6.c -lpcap -lm_  
_gcc -Wall -o frag6 tools/frag6.c -lpcap -lm_  
_gcc -Wall -o icmp6 tools/icmp6.c -lpcap -lm_  
_gcc -Wall -o jumbo6 tools/jumbo6.c -lpcap -lm_  
_gcc -Wall -o na6 tools/na6.c -lpcap -lm_  
_gcc -Wall -o ni6 tools/ni6.c -lpcap -lm_  
_gcc -Wall -o ns6 tools/ns6.c -lpcap -lm_  
_gcc -Wall -o ra6 tools/ra6.c -lpcap -lm_  
_gcc -Wall -o rd6 tools/rd6.c -lpcap -lm_  
_gcc -Wall -o rs6 tools/rs6.c -lpcap -lm_  
_gcc -Wall -o scan6 tools/scan6.c -lpcap -lm_  
_gcc -Wall -o tcp6 tools/tcp6.c -lpcap -lm_

&nbsp;

That&#8217;s it.  If you want to install it in the global environment, to a &#8220;_make install_&#8221;

Now for the good stuff.  The docs are well written for this tool. Here is an example if scanning a local segment in verbose mode:

_(~/Downloads/ipv6-toolkit-v6.8) tardis $ sudo ./scan6 -i en6 -l -e -v_  
_Link-local addresses:_  
_fe80::20d:b9ff:fe68:8ca6 @ 00:0d:b9:68:8c:a6_  
_fe80::264:d6ff:fe25:9704 @ 00:64:d6:25:97:04_  
_fe80::26f:f8ff:fe06:dcb4 @ 00:6f:f8:06:dc:b4_  
_fe80::22cf:80ff:fea8:ec26 @ 20:cf:80:a8:ec:26_  
_fe80::224:86ff:fe9f:c628 @ 00:24:86:9f:c6:28_  
_fe80::267:f2ff:fe52:8574 @ 00:67:f2:52:85:74_  
_fe80::8ed0:f8ff:fe8a:4d29 @ 8c:d0:f8:8a:4d:29_  
_fe80::62fa:cdff:fe86:62bd @ 60:fa:cd:86:62:bd_  
_fe80::629a:ddff:fe45:6c08 @ 60:9a:dd:45:6c:08_

_Global addresses:_

___2001:db8:86c0:24::6 @ 00:0d:b9:68:8c:a6_

_2001:db8:86c0:24:224:86ff:fe9f:c628 @ 00:24:86:9f:c6:28_  
_2001:db8:86c0:24:22cf:80ff:fea8:ec26 @ 20:cf:80:a8:ec:26_  
_2001:db8:86c0:24:26f:f8ff:fe06:dcb4 @ 00:6f:f8:06:dc:b4_  
_2001:db8:86c0:24:267:f2ff:fe52:8574 @ 00:67:f2:52:85:74_  
_2001:db8:86c0:24:62fa:cdff:fe86:62bd @ 60:fa:cd:86:62:bd_  
_2001:db8:86c0:24:8ed0:f8ff:fe8a:4d29 @ 8c:d0:f8:8a:4d:29_  
_2001:db8:86c0:24:629a:ddff:fe45:6c08 @ 60:9a:dd:45:6c:08_

This example,  taken straight from the documentation and run on my local network (with MAC and v6 addresses changed to protect the innocent), will &#8220;Perform host scanning on the local network (“-l” option) using interface “eth0” (“-i” option). Use both ICMPv6 echo requests and unrecognized IPv6 options of type 10xxxxxx (default). Print link- link layer addresses along with IPv6 addresses (“-e” option). Be verbose (“-v” option).&#8221;

One of the interesting things I saw available in this scan6 tool was the ability to narrow down a search based on a known OUI.  If I wanted to search for virtual machines hosted by virtual box or vmware, this command (also taken directly from the docs) would be useful for scanning from a host off net, scanning a network in the lab area:

<div title="Page 6">
  <p>
    <em>sudo ./scan6 -i en0 -d 2001:db8:e00:4000::/64 –tgt-virtual-machines all –ipv4-host 10.17.4.128/25</em>
  </p>
</div>

&nbsp;

<div title="Page 6">
  <p>
    &nbsp;
  </p>
</div>

&nbsp;