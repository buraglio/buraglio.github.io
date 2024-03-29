---
id: 604
title: Basic reference openflow controller VMs running in CentOS 6 for KVM.
date: 2013-04-25T22:48:20-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2013/04/602-revision/
permalink: /2013/04/602-revision/
---
I had been working, off and on, on a how-to for building the daylight controller under CentOS.  Most openflow docs and dev are done under ubuntu or debian, and while those are both fantastic alternatives, there is a huge number of folks that will want or need to use RHEL or CentOS. So, seeing as that is the case, having someone be mindful of that is important.  When I saw the <a href="http://www.dasblinkenlichten.com/installing-opendaylight-on-centos/" target="_blank">write up</a> by <a href="https://twitter.com/blinken_lichten" target="_blank">Jon Langemak</a>, I scrapped mine since his was so much better.  If you&#8217;re not following Jon and reading his blog, you should be.  He&#8217;s a sharp guy with interesting things to say.

[<img class="alignleft size-thumbnail wp-image-603" alt="projectfloodlight-logo-header" src="http://www.forwardingplane.net/wp-content/uploads/2013/04/projectfloodlight-logo-header-150x124.png" width="254" height="209" />](http://www.forwardingplane.net/wp-content/uploads/2013/04/projectfloodlight-logo-header.png)So, I decided that I would take a few of the things I had been working on on my home lab and make them available to the masses.  I&#8217;m a fan of base VMs.  So, seeing that I am working on testing openflow controllers, it made sense in my [constantly racing] mind to make the reference, base level VMs available.  If anyone is interested in the <a href="http://www.projectfloodlight.org/floodlight/" target="_blank">floodlight controller</a> running under CentOS 6.3 built using the method documented <a title="Building a Floodlight OpenFlow controller on CentOS 6" href="http://www.forwardingplane.net/2013/02/building-a-floodlight-openflow-controller-on-centos-6/" target="_blank">here</a>, a KVM image is now available to download from <a href="http://www.forwardingplane.net/wp-content/uploads/vm-images/centos-floodlight-template.tbz" target="_blank">here</a>.  It is, as stated, a KVM images, created by using the method I documented <a title="CentOS KVM Install – Quick Start to a VM" href="http://www.forwardingplane.net/2013/03/centos-kvm-install-quick-start-to-a-vm/" target="_blank">here</a>.    There is a readme file in the archive wth basic instructions.  You&#8217;ll need a basic understanding of <a href="http://www.linux-kvm.org/page/Main_Page" target="_blank">KVM</a> to make it work, or you can try to convert it to something else like vmware, XEN or virtualbox.

I&#8217;ll be adding one of these soon for <a href="http://www.opendaylight.org/" target="_blank">daylight</a> as well.

&nbsp;