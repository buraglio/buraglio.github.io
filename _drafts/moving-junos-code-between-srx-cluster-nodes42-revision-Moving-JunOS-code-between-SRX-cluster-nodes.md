---
id: 241
title: Moving JunOS code between SRX cluster nodes
date: 2011-01-07T20:11:00-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2011/01/42-revision/
permalink: /2011/01/42-revision/
---
Regardless of the fact that there is now a good ISSU-like service for the SRX (named Low-Impact Cluster Upgrade; LICU for short), if you&#8217;re upgrading your Active/Active cluster from something that <span style="font-weight:bold;">isn&#8217;t</span> 10.4, or if you just aren&#8217;t comfortable with how baked LICU actually is, you&#8217;ll need to know how to move the junos code around. This is easy if you have physical access to both nodes, but for those that have.  
This was a problem for me in that our cluster nodes have geographic diversity. In other words, they&#8217;re far apart. Being how I am, I don&#8217;t want to trek all around to hand load code from a USB key and being how the SRX cluster works, I can&#8217;t easily get to node1 over the network since it&#8217;s part of a cluster.

Low and behold, there is a very simple way to move this code around over the control network. Enter our old friend [rcp](http://www.mkssoftware.com/docs/man1/rcp.1.asp).  
Log into node0 and load the code as normal.

<span>node0>file copy scp://buraglio@desktop.domain.edu/Users/buraglio/Downloads/junos-srx5000-10.4R1.9-domestic.tgz /var/tmp/junos-srx5000-10.4R1.9-domestic.tgz</span>

From here, it&#8217;s really easy but will require dropping to the unix (FreeBSD, Yay!) shell so I&#8217;m always careful of what I&#8217;m typing and by all means be careful.

<div>
  <div>
    <span>{primary:node0}</span>
  </div>
  
  <div>
    <span>buraglio@node0> start shell </span>
  </div>
  
  <div>
    <span>% su</span>
  </div>
  
  <div>
    <span>Password: <enter><enter></enter></span>
  </div>
  
  <div>
    <span>root@node0% rcp -T /var/tmp/junos-srx5000-10.4R1.9-domestic.tgz node1:/var/tmp/</span>
  </div>
</div>

<div>
  <span><br /></span>
</div>

Thats pretty much it. Upgrade per the normal active/active procedure. 

[Here](http://kb.juniper.net/InfoCenter/index?page=content&id=KB17410&actp=RSS&smlogin=true) is a Juniper knowledge base article on this procedure for second reference.

<div>
  [[ This is a content summary only. Visit my website for full links, other content, and more! ]]
</div>