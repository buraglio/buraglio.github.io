---
id: 251
title: Updating SRX IDP signatures
date: 2010-09-02T12:16:00-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2010/09/55-revision/
permalink: /2010/09/55-revision/
---
*IDP signatures need to be updated often.  On the SRX platform, there is also the notion of a &#8220;detector&#8221;.  This also meeds to be updated on a regular basis. it seems.  Over the past few weeks, we&#8217;ve needed to update the IDP signatures and detector on our SRX 5800 cluster several times, and the results have normally been fine.  
Updating the IDP signatures has never been **that** big of a problem (see postings about updating stuff on cluster nodes).  But we ran into issues due to the fact that we&#8217;d recently disabled application id to troubleshoot another problem.  This was basically causing all of our updates to fail on node1 (the secondary node) when using our [op script](http://www.juniper.net/techpubs/software/junos/junos82/swconfig82-automation/html/op-scripts-overview.html) to push the updates over (sorry, I can&#8217;t share it). 

A few things that I like to make sure to run before and after all of my SRX work are the following:

<span style="font-family: 'Courier New', Courier, monospace;">show chassis cluster status</span>  
<span style="font-family: 'Courier New', Courier, monospace;">show ospf neighbor brief</span>  
<span style="font-family: 'Courier New', Courier, monospace;">show security idp attack table</span>

If I&#8217;m doing work on the IDP engine, I also want to see the status of that:

<span style="font-family: 'Courier New', Courier, monospace;">request security idp security-package download status</span>  
<span style="font-family: 'Courier New', Courier, monospace;">request security idp security-package install status</span>  
<span style="font-family: 'Courier New', Courier, monospace;">show services application-identification counter</span>*

Anyway, for anyone else running into this odd behavior, to finally update it was a simple matter of deleting app-id before running the updates. 

<span style="font-family: 'Courier New', Courier, monospace;">edit </span>  
<span style="font-family: 'Courier New', Courier, monospace;">delete services application-id</span>  
<span style="font-family: 'Courier New', Courier, monospace;">commit comment &#8220;delete services application-id&#8221; </span>  
<span style="font-family: 'Courier New', Courier, monospace;">request security idp security-package download full-update</span>  
<span style="font-family: 'Courier New', Courier, monospace;">request security idp security-package install </span>  
<span style="font-family: 'Courier New', Courier, monospace;">op instlll-idp-updates</span>

At that point run the status commands <span style="font-family: 'Courier New', Courier, monospace;">request security idp security-package install status</span><span style="font-family: Times, 'Times New Roman', serif;">. It should yield something like </span><span style="font-family: 'Courier New', Courier, monospace;">Done;Attack DB update : successful </span><span style="font-family: Times, 'Times New Roman', serif;">on both nodes.</span><span style="font-family: 'Courier New', Courier, monospace;">  </span>  
<span style="font-family: 'Courier New', Courier, monospace;"><br /></span>  
*It should be noted that Application ID is now in services, whereas I believe it used to be down in security.



<div>
</div>

<div>
</div>

<div>
  [[ This is a content summary only. Visit my website for full links, other content, and more! ]]
</div>