---
id: 74
title: Setting IPv6 precedence under FreeBSD
date: 2010-09-02T12:44:00-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2010/09/54-revision/
permalink: /2010/09/54-revision/
---
I had been discussing [IPv6](http://en.wikipedia.org/wiki/IPv6) address precedence recently and realized that I&#8217;d never really messed with it.  I have a FreeBSD host that has multiple IPv6 addresses, an [EUI-64](http://standards.ieee.org/regauth/oui/tutorials/EUI64.html) address as well as a statically assigned address.  If you don&#8217;t know what IPv6 or [EUI-64](http://standards.ieee.org/regauth/oui/tutorials/EUI64.html) is, I suggest you brush up because [IPv6](http://en.wikipedia.org/wiki/IPv6) is coming and it&#8217;s coming sooner than you thing. 

Using the [ip6addrctl](http://man.freetechsecrets.com/ip6addrctl.8.html) command I can manipulate which  address is preferred for outbound connections. 

<span style="font-family: 'Courier New', Courier, monospace;"><span style="font-size: small;">[buraglio@synack:~ ] ip6addrctl show                                                                                        </span></span>  
<span style="font-family: 'Courier New', Courier, monospace;"><span style="font-size: small;">Prefix                          Prec Label      Use</span></span>  
<span style="font-family: 'Courier New', Courier, monospace;"><span style="font-size: small;">::1/128                           50     0        0</span></span>  
<span style="font-family: 'Courier New', Courier, monospace;"><span style="font-size: small;">::/0                              40     1  1165005</span></span>  
<span style="font-family: 'Courier New', Courier, monospace;"><span style="font-size: small;">2002::/16                         30     2        0</span></span>  
<span style="font-family: 'Courier New', Courier, monospace;"><span style="font-size: small;">::/96                             20     3        0</span></span>  
<span style="font-family: 'Courier New', Courier, monospace;"><span style="font-size: small;">::ffff:0.0.0.0/96                 10     4        0</span></span>  
<span style="font-family: 'Courier New', Courier, monospace;"><span style="font-size: small;">2620:0:e00:4000::/64               1     0       63</span></span>

<div>
</div>

<div>
  This is the default configuration on my FreeBSD 7.1 machine.  Here we can see that I have several IPv6 addresses:
</div>

<div>
</div>

<div>
  <div>
    <span style="font-family: 'Courier New', Courier, monospace;"><span style="font-size: small;">[buraglio@synack:~ ] ifconfig                                                                                               <1215></span></span>
  </div>
  
  <div>
    <span style="font-family: 'Courier New', Courier, monospace;"><span style="font-size: small;">le0: flags=8843<UP,BROADCAST,RUNNING,SIMPLEX,MULTICAST> metric 0 mtu 1500</span></span>
  </div>
  
  <div>
    <span style="white-space: pre;"><span style="font-family: 'Courier New', Courier, monospace;"><span style="font-size: small;"> </span></span></span><span style="font-family: 'Courier New', Courier, monospace;"><span style="font-size: small;">options=8<VLAN_MTU></span></span>
  </div>
  
  <div>
    <span style="white-space: pre;"><span style="font-family: 'Courier New', Courier, monospace;"><span style="font-size: small;"> </span></span></span><span style="font-family: 'Courier New', Courier, monospace;"><span style="font-size: small;">ether 00:0c:29:b6:96:ba</span></span>
  </div>
  
  <div>
    <span style="white-space: pre;"><span style="font-family: 'Courier New', Courier, monospace;"><span style="font-size: small;"> </span></span></span><span style="font-family: 'Courier New', Courier, monospace;"><span style="font-size: small;">inet6 fe80::20c:29ff:feb6:96ba%le0 prefixlen 64 scopeid 0x1 </span></span>
  </div>
  
  <div>
    <span style="white-space: pre;"><span style="font-family: 'Courier New', Courier, monospace;"><span style="font-size: small;"> </span></span></span><span style="font-family: 'Courier New', Courier, monospace;"><span style="font-size: small;">inet6 2620:0:e00:4000::146 prefixlen 64 </span></span>
  </div>
  
  <div>
    <span style="white-space: pre;"><span style="font-family: 'Courier New', Courier, monospace;"><span style="font-size: small;"> </span></span></span><span style="font-family: 'Courier New', Courier, monospace;"><span style="font-size: small;">inet6 </span></span><span style="font-family: 'Courier New', Courier, monospace;"><span style="font-size: small;">2620:0:e00:4000:20c:29ff:feb6:96ba</span></span><span style="font-family: 'Courier New', Courier, monospace;"><span style="font-size: small;"> prefixlen 64 </span></span>
  </div>
  
  <div>
    <span style="white-space: pre;"><span style="font-family: 'Courier New', Courier, monospace;"><span style="font-size: small;"> </span></span></span><span style="font-family: 'Courier New', Courier, monospace;"><span style="font-size: small;">inet 128.174.43.146 netmask 0xffffff80 broadcast 128.174.43.255</span></span>
  </div>
  
  <div>
    <span style="white-space: pre;"><span style="font-family: 'Courier New', Courier, monospace;"><span style="font-size: small;"> </span></span></span><span style="font-family: 'Courier New', Courier, monospace;"><span style="font-size: small;">media: Ethernet autoselect</span></span>
  </div>
  
  <div>
    <span style="white-space: pre;"><span style="font-family: 'Courier New', Courier, monospace;"><span style="font-size: small;"> </span></span></span><span style="font-family: 'Courier New', Courier, monospace;"><span style="font-size: small;">status: active</span></span>
  </div>
</div>

<div>
</div>

<div>
  <span style="font-family: inherit;">Obviously</span> the fe80 address is my link local.  The <span style="font-family: 'Courier New', Courier, monospace; font-size: small;">2620:0:e00:4000::146 </span><span style="font-family: inherit;">is a manually assigned address and </span><span style="font-family: inherit;"><span style="font-size: small;"><span style="font-family: 'Courier New', Courier, monospace;">2620:0:e00:4000:20c:29ff:feb6:96ba</span></span> is my <a href="http://standards.ieee.org/regauth/oui/tutorials/EUI64.html">EUI-64</a> address.</span><span style="font-family: 'Courier New', Courier, monospace; font-size: small;">  </span><span style="font-family: inherit;">I believe the default behavior on FreeBSD is to prefer the manually configured address, which is the behavior that is exhibited when I test it.  </span>
</div>

<div>
  <span style="font-family: 'Courier New', Courier, monospace; font-size: small;"><br /></span>
</div>

<div>
  <span style="font-family: 'Courier New', Courier, monospace;"><span style="font-size: small;">buraglio@synack:~ ] ping6 remote.buraglio.com                                                                              <1218></span></span>
</div>

<div>
  <span style="font-family: 'Courier New', Courier, monospace;"><span style="font-size: small;">PING6(56=40+8+8 bytes) 2620:0:e00:4000::146 &#8211;> 2607:f2f8:4980::2</span></span>
</div>

<div>
  <span style="font-family: 'Courier New', Courier, monospace;"><span style="font-size: small;">16 bytes from 2607:f2f8:4980::2, icmp_seq=0 hlim=47 time=44.454 ms</span></span>
</div>

<div>
  <span style="font-family: 'Courier New', Courier, monospace;"><span style="font-size: small;">16 bytes from 2607:f2f8:4980::2, icmp_seq=1 hlim=47 time=64.172 ms</span></span>
</div>

<div>
  <span style="font-family: 'Courier New', Courier, monospace; font-size: small;"><br /></span>
</div>

<div>
  <span style="font-family: inherit;">results in</span><span style="font-family: 'Courier New', Courier, monospace; font-size: small;"> </span>
</div>

<div>
  <span style="font-family: 'Courier New', Courier, monospace; font-size: small;"><br /></span>
</div>

<div>
  <span style="font-family: 'Courier New', Courier, monospace;"><span style="font-size: small;">[buraglio@collector:~ ] sudo tcpdump ip6 proto 58</span></span>
</div>

<div>
  <span style="font-size: small;"><span style="font-family: 'Courier New', Courier, monospace;"></span></span><br /><span style="font-family: 'Courier New', Courier, monospace;"><span style="font-size: small;"></p> 
  
  <div>
    <span style="font-size: small;">08:30:17.381695 IP6 2620:0:e00:4000::146 > 2607:f2f8:4980::2: ICMP6, echo request, seq 0, length 16</span>
  </div>
  
  <div>
    <span style="font-size: small;">08:30:17.381781 IP6 2607:f2f8:4980::2 > 2620:0:e00:4000::146: ICMP6, echo reply, seq 0, length 16</span>
  </div>
  
  <div>
    <span style="font-size: small;">08:30:18.951558 IP6 2620:0:e00:4000::146 > 2607:f2f8:4980::2: ICMP6, echo request, seq 1, length 16</span>
  </div>
  
  <div>
    <span style="font-size: small;">08:30:18.951641 IP6 2607:f2f8:4980::2 > 2620:0:e00:4000::146: ICMP6, echo reply, seq 1, length 16</span>
  </div>
  
  <div>
  </div>
  
  <div>
    <span style="font-family: Times, 'Times New Roman', serif;">If I change the precedence to prefer the EUI-64 address, it will source that traffic from there, as such:</span>
  </div>
  
  <div>
    <div>
      <span style="font-size: small;">sudo ip6addrctl add 2620:0:e00:4000:20c:29ff:feb6:96ba/64 1 primary </span>                             
    </div>
  </div>
  
  <div>
    and do the experiment again, I see different results.  
  </div>
  
  <p>
    </span></span></div> 
    
    <div>
      <span style="font-family: 'Courier New', Courier, monospace;"><span style="font-size: small;"><br /></span></span>
    </div>
    
    <div>
      <span style="font-family: 'Courier New', Courier, monospace;"><span style="font-size: small;"><br /></span></span>
    </div>
    
    <div>
      <span style="font-family: 'Courier New', Courier, monospace; font-size: small;">  </span>
    </div>
    
    <div>
    </div>