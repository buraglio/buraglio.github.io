---
id: 480
title: 'CentOS KVM Install &#8211; Quick Start to a VM'
date: 2013-03-01T14:38:48-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2013/03/467-revision-4/
permalink: /2013/03/467-revision-4/
---
I&#8217;ve been a virtualization user forever, VMware (Fusion, ESX), VirtualBox, Parallels, whatever.  I&#8217;d not really messed around much with qemu or KVM, but some projects I was working on suggested it for the virtualization mechanism, so I figured I&#8217;d learn it.  Heck, I think the hosting provider  of this blog is using it to provide the VPS that this site runs on.

A few things became obvious pretty quickly:

It&#8217;s very robust.

It&#8217;s got a lot of documentation, but not all of it is straightforward.

It has a lot of pieces needed to make it work efficiently.

Here is what I had to do to get it running on a fresh install of CentOS 6.3.

Install all the dependancies.  And there were many.  Coming from using the VirtualBox CLI, little things that I expected didn&#8217;t work if I didn&#8217;t have this or that installed.

<!--?xml version="1.0" encoding="UTF-8" standalone="no"?-->

_<span style="font-family: Verdana;">yum install -y qemu-kvm.x86_64 qemu-kvm-tools.x86_64 </span>kvm libvirt bridge-utils tunctl python-virtinst.noarch avahi_

Restart the deamons

_/etc/init.d/messagebus restart_  
 _/etc/init.d/avahi-daemon restart_  
 _/etc/init.d/libvirtd restart_

Make the new daemons start at boot:

<!--?xml version="1.0" encoding="UTF-8" standalone="no"?-->

<div>
  <span style="font-family: Verdana;">/sbin/chkconfig messagebus on</span>
</div>

<div>
  <span style="font-family: Verdana;">/sbin/chkconfig avahi-daemon on</span>
</div>

<div>
</div>

<div>
  I want to bridge rather than NAT.  My VMs need to have a public (or same LAN segment) address as the rest of the hosts for external management and availability of inbound services.  For this, we need to adjust the interfaces.  I want to run the bridge on a second interface and keep the host system management on a dedicated interface.
</div>

<div>
</div>

<div>
  <!--?xml version="1.0" encoding="UTF-8" standalone="no"?--></p> 
  
  <div>
    <em><span style="font-family: Verdana;">vi /etc/sysconfig/network-scripts/ifcfg-eth1</span></em>
  </div>
  
  <div>
  </div>
  
  <div>
    <div>
      Your file should look something like this when done:
    </div>
    
    <p>
      <em><span style="font-family: Verdana;">DEVICE=&#8221;eth1&#8243;</span></em><br /> <em> <span style="font-family: Verdana;">HWADDR=&#8221;c0:ff:ee:c0:ff:ee&#8221; # <strong>(leave this as your MAC address)</strong></span></em><br /> <em> <span style="font-family: Verdana;">NM_CONTROLLED=&#8221;yes&#8221;</span></em><br /> <em> <span style="font-family: Verdana;">BRIDGE=br0</span></em><br /> <em> <span style="font-family: Verdana;">ONBOOT=&#8221;yes&#8221;</span></em><br /> <em> <span style="font-family: Verdana;">UUID=&#8221;a9c26927-7650-42e9-a86a-1ae1227eac4b&#8221; # <strong>(leave this as your UUID)</strong></span></em>
    </p>
  </div>
  
  <div>
    <em><span style="font-family: Verdana;"> </span></em>
  </div>
  
  <div>
    <em><span style="font-family: Verdana;">vi /etc/sysconfig/network-scripts/ifcfg-br0</span></em>
  </div>
  
  <div>
  </div>
  
  <div>
    Your file should look something like this when done:
  </div>
  
  <div>
  </div>
  
  <p>
    <em><span style="font-family: Verdana;">DEVICE=&#8221;eth1&#8243;</span></em>
  </p>
</div>

<div>
  <em><span style="font-family: Verdana;">HWADDR=&#8221;de:ad:be:ef:ca:fe&#8221; # <strong>(leave this as your MAC address)</strong></span></em>
</div>

<div>
  <em><span style="font-family: Verdana;">NM_CONTROLLED=&#8221;yes&#8221;</span><span style="font-family: Verdana;">BRIDGE=br0</span></em>
</div>

<div>
  <em><span style="font-family: Verdana;">ONBOOT=&#8221;yes&#8221;</span></em>
</div>

<div>
  <em><span style="font-family: Verdana;">UUID=&#8221;a9c26927-7650-42e9-a86a-1ae1227eac4b&#8221; # <strong>(leave this as your UUID)</strong></span></em></p> 
  
  <div>
  </div>
  
  <div>
    Restart the network to make it active.
  </div>
  
  <div>
  </div>
  
  <div>
    <em><span style="font-family: Verdana;">service network restart</span></em>
  </div>
</div>

You&#8217;re going to use <!--?xml version="1.0" encoding="UTF-8" standalone="no"?--> Virt tools and virsh to manipulate the guests.  I tried it a few other ways and this seems far more supportable.  I wanted to install a CentOS 6.3 guest, I grabbed the install media from a 

<a href="http://cosmos.cites.illinois.edu/pub/centos/6.3/isos/x86_64/" target="_blank">local mirror</a>.  I have a volume mounted as /services that I keep stuff in.

_mkdir /services/vm/template-host_  
 _cd /services/vm/template-host_  
 _wget http://cosmos.cites.illinois.edu/pub/centos/6.3/isos/x86\_64/CentOS-6.3-x86\_64-bin-DVD1.iso_

Now use the virt-install command to boot the system with the following parameters:

2G of RAM

50G disk named disk.img

Console redirected to a VNC instance on port 5901

Network interface attached to br0

4 CPUs

CDROM points to install image

_virt-install &#8211;name template-host &#8211;ram 2048 &#8211;disk /home/vm/template-host/disk.img &#8211;size=50 &#8211;graphics vnc,port=5901 &#8211;network bridge=br0 &#8211;vcpus=4 &#8211;os-type=linux &#8211;cdrom=/home/vm/Install\_Media/CentOS-6.3-x86\_64-bin-DVD1.iso_

Now, to connect to the console, you&#8217;ll need to tunnel VNC over ssh.  This can be adjusted, but that&#8217;s outside of the scope of this.

I like to redirect real port numbers for my own sanity.

_ssh -N -p 22 -c 3des buraglio@vmhost -L 5901/localhost/5901_

The above command will redirect localhost port 5901 to port 5901 on the host vmhost

Connect to the VNC server:

<p style="text-align: center;">
  <a href="http://www.forwardingplane.net/wp-content/uploads/2013/03/Screen-Shot-2013-03-01-at-2.00.37-PM.png"><img class="aligncenter  wp-image-470" alt="Screen Shot 2013-03-01 at 2.00.37 PM" src="http://www.forwardingplane.net/wp-content/uploads/2013/03/Screen-Shot-2013-03-01-at-2.00.37-PM.png" width="404" height="251" srcset="http://www.forwardingplane.net/wp-content/uploads/2013/03/Screen-Shot-2013-03-01-at-2.00.37-PM.png 505w, http://www.forwardingplane.net/wp-content/uploads/2013/03/Screen-Shot-2013-03-01-at-2.00.37-PM-300x186.png 300w" sizes="(max-width: 404px) 100vw, 404px" /></a>
</p>

<p style="text-align: left;">
  Once connected you should drop right into the console of the KVM instance. Install as a normal system at that point.  Once installed It&#8217;ll appear as a normal host console.
</p>

<p style="text-align: center;">
  <a href="http://www.forwardingplane.net/wp-content/uploads/2013/03/Screen-Shot-2013-03-01-at-2.01.21-PM.png"><img class="aligncenter  wp-image-469" alt="Screen Shot 2013-03-01 at 2.01.21 PM" src="http://www.forwardingplane.net/wp-content/uploads/2013/03/Screen-Shot-2013-03-01-at-2.01.21-PM.png" width="430" height="253" srcset="http://www.forwardingplane.net/wp-content/uploads/2013/03/Screen-Shot-2013-03-01-at-2.01.21-PM.png 717w, http://www.forwardingplane.net/wp-content/uploads/2013/03/Screen-Shot-2013-03-01-at-2.01.21-PM-300x176.png 300w, http://www.forwardingplane.net/wp-content/uploads/2013/03/Screen-Shot-2013-03-01-at-2.01.21-PM-550x323.png 550w" sizes="(max-width: 430px) 100vw, 430px" /></a>
</p>

<p style="text-align: left;">
  I found virsh to be the most useful for manipulating the virtual machine.
</p>

<p style="text-align: left;">
  <em>[root@behemoth Install_Media]# virsh list</em>
</p>

 _Id            Name                                      State_  
_&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;-_  
 _9              template-host                         running_

&nbsp;

Helpful commands I found after 30 minutes of poking around and playing with virsh:

_virsh list_ &#8211;show the list of virtual machines

_virsh destroy_ <vm name> &#8211;hard shut down a host (I believe)

_virsh undefine_ <vm name> &#8211;remove the VM from registration &#8211;this one was hard for me to find.

&nbsp;

<a title="KVM virsh command reference" href="http://www.forwardingplane.net/unix/kvm-virsh-command-referenc/" target="_blank">Here</a> is a complete list of the commands.