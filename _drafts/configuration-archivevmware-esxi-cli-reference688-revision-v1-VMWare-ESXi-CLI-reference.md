---
id: 1614
title: VMWare ESXi CLI reference
date: 2019-02-19T08:38:55-06:00
author: Nick Buraglio
layout: revision
guid: https://www.forwardingplane.net/2019/02/688-revision-v1/
permalink: /2019/02/688-revision-v1/
---
All of these commands require ssh to be enabled on the VMware host and were tested on 5.1.

Power off a VM

<pre class="wp-block-preformatted">vim-cmd vmsvc/power.getstate</pre>

List power state of VM:

<pre class="wp-block-preformatted">vim-cmd vmsvc/power.of</pre>

Power on VM

<pre class="wp-block-preformatted">vim-cmd vmsvc/power.on</pre>

List all VMs:

<pre class="wp-block-preformatted">vim-cmd vmsvc/getallvms</pre>

Other important commands under vmsvc:

<pre class="wp-block-preformatted">acquiremksticket get.snapshotinfo<br />acquireticket get.spaceNeededForConsolidation<br />connect get.summary<br />convert.toTemplate get.tasklist<br />convert.toVm getallvms<br />createdummyvm gethostconstraints<br />destroy login<br />device.connection logout<br />device.connusbdev message<br />device.disconnusbdev power.getstate<br />device.diskadd power.hibernate<br />device.diskaddexisting power.off<br />device.diskremove power.on<br />device.getdevices power.reboot<br />device.toolsSyncSet power.reset<br />device.vmiadd power.shutdown<br />device.vmiremove power.suspend<br />devices.createnic power.suspendResume<br />disconnect queryftcompat<br />get.capability reload<br />get.config setscreenres<br />get.config.cpuidmask snapshot.create<br />get.configoption snapshot.dumpoption<br />get.datastores snapshot.get<br />get.disabledmethods snapshot.remove<br />get.environment snapshot.removeall<br />get.filelayout snapshot.revert<br />get.filelayoutex snapshot.setoption<br />get.guest tools.cancelinstall<br />get.guestheartbeatStatus tools.install<br />get.managedentitystatus tools.upgrade<br />get.networks unregister<br />get.runtime upgrade</pre>