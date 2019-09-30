---
id: 1607
title: Mikrotik OpenVPN server
date: 2019-02-18T14:14:40-06:00
author: Nick Buraglio
layout: revision
guid: https://www.forwardingplane.net/2019/02/1606-revision-v1/
permalink: /2019/02/1606-revision-v1/
---
Mikrotik is one of my favorite routing and MPLS platforms for doing lab and small ISP work. This one is pretty darned easy if you&#8217;re willing to use self-signed certificates, and pretty trivial to add legitimate certificates if you are so inclined. 

<pre class="wp-block-preformatted">/certificate add name=ca common-name=ca key-usage=key-cert-sign,crl-sign<br />/certificate sign ca ca-crl-host=10.255.255.4 name=ca<br />/certificate export-certificate ca<br />/certificate add name=gw-dsl common-name=gw.yourcompany.com<br />/certificate add name=vpnclient1 common-name=client1<br />/certificate sign gw-dsl ca=ca name=gw.yourcompany.com<br />/certificate sign vpnclient1 ca=ca name=client1 <br />/ip pool add name=ovpn-pool range=10.2.98.2-10.2.98.19<br />/ppp profile add name=ovpn local-address=10.2.98.1 remote-address=ovpn-pool<br />/ppp secret add name=buraglio profile=ovpn password=ExamplePasswordDude<br />/interface ovpn-server server set enabled=yes certificate=server auth=sha1 cipher=aes256 port=1194 netmask=24 require-client-certificate=yes mode=ip<br />/certificate export-certificate client1  export-passphrase=ExamplePasswordDude</pre>

Largely based on [this example](https://delphinus.qns.net/xwiki/bin/view/Blog/Mikrotik%20OpenVPN%20in%2090%20seconds)