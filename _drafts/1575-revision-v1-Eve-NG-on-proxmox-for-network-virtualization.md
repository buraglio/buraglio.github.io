---
id: 1579
title: Eve-NG on proxmox for network virtualization
date: 2019-01-16T09:27:17-06:00
author: Nick Buraglio
layout: revision
guid: https://www.forwardingplane.net/2019/01/1575-revision-v1/
permalink: /2019/01/1575-revision-v1/
---
CPU type “host” for proper nested virtualization

 

https://pve.proxmox.com/wiki/Nested_Virtualization

 

Converting images

 

qemu-img convert -f vmdk -O qcow2 vmx-nested-18.2R1.9-4.vmdk vmx-18.2R1.9-4/hda.qcow2