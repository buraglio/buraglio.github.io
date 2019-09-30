---
id: 690
title: VMWare ESX CLI reference
date: 2013-06-30T08:07:13-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2013/06/688-revision/
permalink: /2013/06/688-revision-v1/
---
List all VMs:  
vim-cmd vmsvc/getallvms

List power state of VM:  
vim-cmd vmsvc/power.getstate <VM ID>

Power on VM  
vim-cmd vmsvc/power.on <VM ID>

Power off VM  
vim-cmd vmsvc/power.off <VM ID>