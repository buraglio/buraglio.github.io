---
id: 1014
title: Linux Network Namespaces for multihomed hosts
date: 2014-05-20T14:05:24-06:00
author: Nick Buraglio
layout: post
guid: http://www.forwardingplane.net/?p=1014
permalink: /?p=1014
categories:
  - Musings
---
sudo ip netns exec uc2b ip link list  
ip netns exec uc2b ifconfig uc2b1 192.80.111.58/24 up  
sudo ip netns exec uc2b ifconfig uc2b1 192.80.111.58/24 up  
sudo ovs-vsctl add-port br-int uc2b1  
ip netns exec uc2b ip link set uc2b1 up  
sudo ip netns exec uc2b ip link set uc2b1 up  
sudo brctl addbr uc2bbr  
sudo brctl ifbr uc2bbr uc2b1  
sudo brctl addif uc2bbr uc2b1  
sudo brctl delbr uc2bbr  
sudo ovs-vsctl add-port br-int uc2b1  
sudo ovs-vsctl add-port br-int uc2b1  
sudo ovs-vsctl add-br uc2bbr uc2b1  
sudo ovs-vsctl add-br uc2bbr  
sudo ovs-vsctl add-port uc2bbr uc2b1  
sudo ovs-vsctl add-port uc2bbr eth1  
sudo ip netns exec uc2b ifconfig uc2b1 192.80.111.58/24 up  
sudo ovs-vsctl add-port uc2bbr uc2b0  
sudo ip netns exec uc2b ip link set uc2b1 up  
sudo ip netns exec uc2b ping 192.80.111.58  
sudo ip netns exec uc2b ifconfig uc2b1 up  
sudo ip netns exec uc2b ifconfig uc2b0 up  
sudo ip netns exec uc2b arp -an  
sudo ip netns exec uc2b arp  
sudo ip netns exec uc2b ip route  
sudo ip netns exec uc2b ip route add 0.0.0.0 192.80.111.1  
sudo ip netns exec uc2b ip route add 0.0.0.0 to 192.80.111.1  
sudo ip netns exec uc2b ip route add 0.0.0.0/0 to 192.80.111.1  
sudo ip netns exec uc2b ip route add default via 192.80.111.1  
sudo ip netns exec uc2b ip route  
sudo ip netns exec uc2b ping 192.80.111.1  
sudo ovs-vsctl list-br uc2bbr  
sudo ovs-vsctl list-ports uc2bbr  
sudo ip netns exec uc2b ifconfig  
sudo ip netns exec uc2b ping  
history | grep uc2b  
sudo ip netns exec uc2b ip link list  
sudo ip netns exec uc2b ip link list  
history | grep uc2b  
ip netns exec uc2b ip link set uc2b1 up  
sudo ip netns exec uc2b ip link set uc2b1 up  
sudo ip netns exec uc2b ip link set eth1 up  
sudo ip netns exec uc2b ip link set uc2b0 up  
sudo ip netns exec uc2b ip link list  
sudo ip link add uc2b0 type veth peer name uc2b1  
sudo ip netns exec uc2b ip link list  
sudo ip netns exec uc2b ifconfig uc2b0 192.80.111.59/24 up  
sudo ip netns exec uc2b ip link list  
history | grep uc2b  
sudo ovs-vsctl add-port uc2bbr uc2b0  
history | grep uc2b0  
history | grep uc2b1  
sudo ip netns exec uc2b ip link list  
ip link set uc2b1 netns uc2b  
ip link set uc2bbr netns uc2b  
sudo ip link set uc2bbr netns uc2b  
sudo ip link set uc2bbr netns uc2b0  
sudo ip link set uc2b0 netns uc2b  
sudo ip netns exec uc2b ip link list  
sudo ip netns exec uc2b ifconfig uc2bbr up  
sudo ip netns exec uc2b ifconfig uc2b0 up  
sudo ip netns exec uc2b ip link list  
sudo ip netns exec uc2b ping arpo  
sudo ip netns exec uc2b ping arp -an  
sudo ip netns exec uc2b arp -an  
sudo ip netns exec uc2b ping 192.80.111.1  
sudo ip netns exec uc2b ping 4.2.2.1  
sudo ip netns exec uc2b traceroute 4.2.2.1  
sudo ip netns exec uc2b /usr/sbin/sshd

<div class="sharedaddy sd-sharing-enabled">
  <div class="robots-nocontent sd-block sd-social sd-social-icon-text sd-sharing">
    <h3 class="sd-title">
      Share this:
    </h3>
    
    <div class="sd-content">
      <ul>
        <li class="share-twitter">
          <a rel="nofollow noopener noreferrer" data-shared="sharing-twitter-1014" class="share-twitter sd-button share-icon" href="http://www.forwardingplane.net/?p=1014&share=twitter" target="_blank" title="Click to share on Twitter"><span>Twitter</span></a>
        </li>
        <li class="share-email">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-email sd-button share-icon" href="http://www.forwardingplane.net/?p=1014&share=email" target="_blank" title="Click to email this to a friend"><span>Email</span></a>
        </li>
        <li class="share-print">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-print sd-button share-icon" href="http://www.forwardingplane.net/?p=1014" target="_blank" title="Click to print"><span>Print</span></a>
        </li>
        <li class="share-linkedin">
          <a rel="nofollow noopener noreferrer" data-shared="sharing-linkedin-1014" class="share-linkedin sd-button share-icon" href="http://www.forwardingplane.net/?p=1014&share=linkedin" target="_blank" title="Click to share on LinkedIn"><span>LinkedIn</span></a>
        </li>
        <li class="share-facebook">
          <a rel="nofollow noopener noreferrer" data-shared="sharing-facebook-1014" class="share-facebook sd-button share-icon" href="http://www.forwardingplane.net/?p=1014&share=facebook" target="_blank" title="Click to share on Facebook"><span>Facebook</span></a>
        </li>
        <li class="share-reddit">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-reddit sd-button share-icon" href="http://www.forwardingplane.net/?p=1014&share=reddit" target="_blank" title="Click to share on Reddit"><span>Reddit</span></a>
        </li>
        <li class="share-tumblr">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-tumblr sd-button share-icon" href="http://www.forwardingplane.net/?p=1014&share=tumblr" target="_blank" title="Click to share on Tumblr"><span>Tumblr</span></a>
        </li>
        <li class="share-pinterest">
          <a rel="nofollow noopener noreferrer" data-shared="sharing-pinterest-1014" class="share-pinterest sd-button share-icon" href="http://www.forwardingplane.net/?p=1014&share=pinterest" target="_blank" title="Click to share on Pinterest"><span>Pinterest</span></a>
        </li>
        <li class="share-pocket">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-pocket sd-button share-icon" href="http://www.forwardingplane.net/?p=1014&share=pocket" target="_blank" title="Click to share on Pocket"><span>Pocket</span></a>
        </li>
        <li class="share-end">
        </li>
      </ul>
    </div>
  </div>
</div>