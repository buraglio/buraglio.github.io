---
id: 1635
title: Enabling LLDP
date: 2019-03-06T20:05:16-06:00
author: Nick Buraglio
excerpt: Configuration archive for enabling LLDP on various platforms such as Nokia SROS, JunOS, Mikrotik ROS, Linux
layout: revision
guid: https://www.forwardingplane.net/2019/03/1632-revision-v1/
permalink: /2019/03/1632-revision-v1/
---
Enabling LLDP can aid in understanding network and system topologies, I am very much in favor of running it and largely dismiss the perceived security issues surrounding it, when done correctly and with full knowledge of what it is being enabled. 

Enable LLDP on a SROS based Nokia (formerly Alcatel-Lucent). It is per physical port, so replace 1/1/1 with your physical port and replicate on every port you want it to run on

<pre class="wp-block-preformatted">/configure port 1/1/1 ethernet lldp dest-mac nearest-bridge tx-mgmt-address system <br />/configure port 1/1/1 ethernet lldp dest-mac nearest-bridge tx-tlvs port-desc sys-name sys-cap sys-desc <br />/configure port 1/1/1 ethernet lldp dest-mac nearest-bridge admin-status tx-rx </pre>

Enable LLDP on a Juniper is by interface or global

<pre class="wp-block-preformatted">set protocols lldp advertisement-interval 30 <br />set protocols lldp interface all <br /></pre>

Mikrotik switch to LLDP as the discovery protocol in 6.something. MNDP/LLDP is on by default but can be changed by configuring the discover-interface-list 

<pre class="wp-block-preformatted">/ip neighbor discover-interface-list</pre>

Brocade VDX. This is a little dated but I suspect it&#8217;s still correct. 

<pre class="wp-block-preformatted">conf t <br />protocol lldp <br />&nbsp;hello 180 <br />&nbsp;advertise dcbx-tlv <br />&nbsp;advertise optional-tlv management-address <br />&nbsp;advertise optional-tlv port-description <br />&nbsp;advertise optional-tlv system-capabilities <br />&nbsp;advertise optional-tlv system-description <br />&nbsp;advertise optional-tlv system-name <br />&nbsp;system-name dnoc960-sw1-mgmt <br />&nbsp;system-description Brocade VDX switch <br />exit<br />copy running-config startup-config </pre>

Ubuntu / Debian Linux

<pre class="wp-block-preformatted">apt install lldpd<br />service lldpd start</pre>