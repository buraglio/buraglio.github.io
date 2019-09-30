---
id: 1708
title: ElastiFlow Base VM
date: 2019-09-08T11:57:51-06:00
author: Nick Buraglio
layout: revision
guid: https://www.forwardingplane.net/2019/09/1706-revision-v1/
permalink: /2019/09/1706-revision-v1/
---
Included here is a vanilla Ubuntu 18 LTS VM with a basic [Elastiflow](https://github.com/robcowart/elastiflow) install. This includes all of the components of an ElasticStack plus the front end pieces of the ElastiFlow project. Most of the install is based on [this](https://www.catapultsystems.com/blogs/install-elastiflow-on-ubuntu-18-04-part-1/) how-to.&nbsp;

Included in the image is also a base install of NGINX and certbot so that you can reverse proxy the access and have a valid SSL certificate.&nbsp;

This was build and validated on Proxmox 6.0.6 but should be able to run on VMWare as well with a bit of qemu-img conversion. As expected, ElastiFlow (and ElasticStack) is fairly resource hungry, 16G of Memory and a handful of CPU cores is the bare minimum to run this with any real efficiency. Ubuntu 18 has changed how the networking is setup &#8211; it is all located in /etc/netplan/ now.     


Login Information:

<pre class="wp-block-preformatted">User Name: root
Password: elastiflow
Privileged user: elastiflow
Password: elastiflow<br /></pre>

Default IP addresses:

<pre class="wp-block-preformatted">10.255.255.5/27
2001:db8:ffff:2::5/64</pre>

Download the image [here](https://drive.google.com/open?id=1ga_Pj2j6h1ce9rcT7jQjncpVjLIC4X4t).