---
id: 458
title: IPv6 Toolkit 1.3 fun
date: 2013-02-19T00:23:18-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2013/02/457-revision/
permalink: /2013/02/457-revision/
---
Recently <a href="http://www.si6networks.com/tools/ipv6toolkit/" target="_blank">SI6 released the IPv6 Toolkit 1.3 </a>  This release is on the heels of this IETF draft

&nbsp;

It&#8217;s pretty straightforward to build on a Mac running 10.8 (assuming you have the Developers Tools and CLI support added).

_(~/Downloads/ipv6-toolkit-v1.3) ubermini $ make_  
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