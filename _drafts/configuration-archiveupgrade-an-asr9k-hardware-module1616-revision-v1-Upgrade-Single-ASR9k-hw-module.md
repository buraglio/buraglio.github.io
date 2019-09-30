---
id: 1617
title: Upgrade Single ASR9k hw-module
date: 2019-02-20T13:58:08-06:00
author: Nick Buraglio
layout: revision
guid: https://www.forwardingplane.net/2019/02/1616-revision-v1/
permalink: /2019/02/1616-revision-v1/
---
ASR9k is a powerful device but management may be daunting to anyone not familiar with IOS-XR. Inserting new line cards in may require a manual upgrade of the module to match the current running code on the chassis

Show all slow and firmware details: 

<pre class="wp-block-preformatted">show hw-module fpd location <em>rack/slot/subslot</em></pre>

In the admin prompt: 

<pre class="wp-block-preformatted">upgrade hw-module fpd all location 0/RSP1/CPU0</pre>

  
During the upgrade, this is the output, it will take a bit of time to perform the update. You may also need to upgrade things like fan trays, etc. 

<pre class="wp-block-preformatted">RP/0/RSP0/CPU0:core-9k(admin)#upgrade hw-module fpd all location 0/RSP1/CPU0Mon Feb 18 09:56:49.201 CST<br />***** UPGRADE WARNING MESSAGE: *****  <br />*  This upgrade operation has a maximum timout of 90 minutes.  *  <br />*  If you are executing the cmd for one specific location and  *  <br />*  card in that location reloads or goes down for some reason  *  <br />*  you can press CTRL-C to get back the RP's prompt.           *  <br />*  If you are executing the cmd for _all_ locations and a node *  <br />*  reloads or is down please allow other nodes to finish the   *  <br />*  upgrade process before pressing CTRL-C.                     *<br />% RELOAD REMINDER: <br /> - The upgrade operation of the target module will not interrupt its normal    operation. However, for the changes to take effect, the target module    will need to be manually reloaded after the upgrade operation. This can    be accomplished with the use of "hw-module &lt;target> reload" command.  <br />- If automatic reload operation is desired after the upgrade, please use    the "reload" option at the end of the upgrade command.  <br />- The output of "show hw-module fpd location" command will not display    correct version information after the upgrade if the target module is    not reloaded.<br /><br />NOTE: Chassis CLI will not be accessible while upgrade is in progress.</pre>