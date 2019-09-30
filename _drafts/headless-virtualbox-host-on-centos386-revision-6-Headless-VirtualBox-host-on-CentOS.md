---
id: 403
title: Headless VirtualBox host on CentOS
date: 2013-01-31T11:55:51-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2013/01/386-revision-6/
permalink: /2013/01/386-revision-6/
---
Starting from a base CentOS system with nothing configured, and referencing the <a href="http://wiki.centos.org/HowTos/Virtualization/VirtualBox" target="_blank">CentOS wiki</a>, here is how I like to set up a headless virtualbox environment:

Disable selinux. It&#8217;s overly cumbersome and is enabled by default in CentOS.  I like to permanently disable it even though the default is permissive.  I ride the edge, I know.

<pre>vi /etc/selinux/config</pre>

<div>
   and change
</div>

<pre>SELINUX=enabled</pre>

<div>
  to
</div>

<pre>SELINUX=disabled</pre>

<div>
  Then reboot.
</div>

Using the methodology I originally found found <a href="http://stackoverflow.com/questions/14016286/how-to-programmatically-install-the-latest-epel-release-rpm-without-knowing-its" target="_blank">here</a>, I like to install the epel repo using this method:

<pre>cat &lt;&lt;EOM &gt;/etc/yum.repos.d/epel-bootstrap.repo
 [epel]
 name=Bootstrap EPEL
 mirrorlist=http://mirrors.fedoraproject.org/mirrorlist?repo=epel-\$releasever&arch=\$basearch
 failovermethod=priority
 enabled=0
 gpgcheck=0
 EOM</pre>

<pre>yum --enablerepo=epel -y install epel-release
 rm -f /etc/yum.repos.d/epel-bootstrap.repo</pre>

Install rpmforge repo

<pre>rpm --import http://apt.sw.be/RPM-GPG-KEY.dag.txt
 rpm -Uvh http://packages.sw.be/rpmforge-release/rpmforge-release-0.5.2-2.el6.rf.x86_64.rpm
 yum clean all</pre>

Install the virtualbox repo

<pre>yum install -y wget
cd /etc/yum.repos.d
wget http://download.virtualbox.org/virtualbox/rpm/rhel/virtualbox.repo
yum update</pre>

<pre></pre>

Now the interesting bits, lets get to the vbox install.  Although we;ve enabled dkms, I like to also install as if we didn&#8217;t.  It populated the system with the pieces we need in a way that Im used to.  I&#8217;m not a sysadmin by day, so this may be redundant.  YMMV, etc.   First install the Development Tools. There are a lot here, it may take a bit depending on machine specs and connectivity. 

<pre>yum groupinstall "Development Tools"
yum install VirtualBox-4.2</pre>

Then start up the service and you should see something like this:

<pre>service vboxdrv setup
Stopping VirtualBox kernel modules [ OK ]
Uninstalling old VirtualBox DKMS kernel modulesError! There are no instances of module: vboxhost
4.2.6 located in the DKMS tree.
 [ OK ]
Trying to register the VirtualBox kernel modules using DKMS
 [ OK ]
Starting VirtualBox kernel modules [ OK ]</pre>

<pre></pre>

At this point you&#8217;ve got virtualbox done and installed. Now, the interesting part begins: VMs. I have a centos template that I built on my laptop.  It&#8217;s got the setting I like and I can just import it.  You can also build a new one, but that&#8217;s for a different post.  I moved the template via scp over to the newly anointed VM host. Now, I just need to import it and I can start cloning.  <a href="http://www.virtualbox.org/manual/ch08.html" target="_blank">vboxmanage</a>is the command we&#8217;re going to be utilizing heavily and it&#8217;s really powerful.  

<pre>vboxmanage import /home/buraglio/centos-63-template.ova</pre>

<pre>0%...10%...20%...30%...40%...50%...60%...70%...80%...90%...100%
Interpreting /home/buraglio/centos-63-template.ova...
OK.
Disks: vmdisk1 150 1359413248 http://www.vmware.com/interfaces/specifications/vmdk.html#streamOptimized centos-63-template-disk1.vmdk 512919552 -1 
Virtual system 0:
 0: Suggested OS type: "Linux26_64"
 (change with "--vsys 0 --ostype &lt;type&gt;"; use "list ostypes" to list all possible values)
 1: Suggested VM name "centos-63-template"
 (change with "--vsys 0 --vmname &lt;name&gt;")
 2: Number of CPUs: 2
 (change with "--vsys 0 --cpus &lt;n&gt;")
 3: Guest memory: 4096 MB
 (change with "--vsys 0 --memory &lt;MB&gt;")
 4: Network adapter: orig ur1-vm1 72.36.126.200/29, config 5, extra type=Bridged
 5: CD-ROM
 (disable with "--vsys 0 --unit 5 --ignore")
 6: SCSI controller, type LsiLogic
 (change with "--vsys 0 --unit 6 --scsitype {BusLogic|LsiLogic}";
 disable with "--vsys 0 --unit 6 --ignore")
 7: IDE controller, type PIIX4
 (disable with "--vsys 0 --unit 7 --ignore")
 8: IDE controller, type PIIX4
 (disable with "--vsys 0 --unit 8 --ignore")
 9: Hard disk image: source image=centos-63-template-disk1.vmdk, target path=/home/buraglio/VirtualBox VMs/centos-63-template/centos-63-template-disk1.vmdk, controller=6;channel=0
 (change target path with "--vsys 0 --unit 9 --disk path";
 disable with "--vsys 0 --unit 9 --ignore")
0%...10%...20%...30%...40%...50%...60%...70%...80%...90%...100%
Successfully imported the appliance.</pre>

<pre></pre>

It&#8217;s there. you should now have a folder in your home directory that has the VM in it. 

<pre></pre>

<pre>ls -la VirtualBox\ VMs/</pre>

<pre>total 12
drwx------ 3 buraglio buraglio 4096 Jan 29 20:23 .
drwx------. 4 buraglio buraglio 4096 Jan 29 20:23 ..
drwx------ 2 buraglio buraglio 4096 Jan 29 20:23 centos-63-template</pre>

to really make this useful, I clone all the VMs to the names I want and don&#8217;t use the template at all.

Now list the vms to verify what you have:

<pre>vboxmanage list vms
"centos-63-template" {4875b540-5514-4d0b-bba8-ce255b7f44a2}</pre>

We have one VM named &#8220;centos-63-template&#8221;, which is exactly what I wanted. Now clone this VM to the first usable VM, I&#8217;m building a floodlight OpenFlow controller, so I&#8217;ll name it accordingly.

<pre>vboxmanage clonevm centos-63-template --name floodlight1 --register
0%...10%...20%...30%...40%...50%...60%...70%...80%...90%...100%
Machine has been successfully cloned as "floodlight1"</pre>

&nbsp;

Now list the vms to make sure it is listed:

<pre>vboxmanage list vms


<pre>"centos-63-template" {4875b540-5514-4d0b-bba8-ce255b7f44a2}


<pre>"floodlight1" {8fb4f03d-d117-43d5-b4bf-24cdcc481686}</pre>


<p>
  Now here is the part I really like about virtualbox headless mode (and yes, I know others like qemu and xen can do this), when a virtual machine is started in headless mode, the console of that host can be redirected to an RDP instance.  This makes it very convenient to manage systems on an out of band network like an isolated vlan or other non-routed or non-publically available network.  It also makes it very convenient for spinning up a new VM that doesn't have an IP stack configured.  Or, if you have a bad day and typo a host firewall rule or network config file.  This has saved me a trip more than one time.  
</p>


<pre>vboxheadless -startvm floodlight1 -vrde on -vrdeproperty port=5999 </pre>