---
id: 237
title: Sync catalogs (iPhoto, iTunes) on a mac
date: 2011-02-18T06:46:00-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2011/02/39-revision/
permalink: /2011/02/39-revision/
---
<div>
  <div>
    <div>
      I have huge iPhoto and iTunes catalogs. This can present a problem for both loading the applications and for backup. I have learned to deal with the Application load times, but backups are very important to me.
    </div>
    
    <div>
    </div>
    
    <div>
      I&#8217;d gone through the iPhoto backup process and restore more than once, and I didn&#8217;t like the fact that I didn&#8217;t have an offsite backup, so I paid for a flickr pro account ($24/yr, supports iPhoto export and RAW format). I had been simply copying my iTunes over to my NAS for a long time (as well as using Time Machine), but that became a chore because I had not automated it.
    </div>
    
    <div>
    </div>
    
    <div>
      After about a month of off-and-on searching, I finally went back to my UNIX roots and decided on rsync.
    </div>
    
    <div>
      You simply can&#8217;t beat rsync.
    </div>
    
    <div>
      I wrote a very simple shell script to call from cron every night to sync whatever IU thought I needed to sync to my NAS (it works to any other source, really, due to rsync&#8217;s flexibility).
    </div>
  </div>
</div>

<div>
  This is my simple rsync script:
</div>

<div>
  </p> 
  
  <div style="font-size: small; ">
  </div>
  
  <div>
    <div>
      <span>#!/bin/sh</span>
    </div>
    
    <div>
      <span># Sync catalogs to externally mounted volume.</span>
    </div>
    
    <div>
      <span># nick@buraglio.com</span>
    </div>
    
    <div>
      <span><br /></span>
    </div>
    
    <div>
      <span>RSYNC=&#8217;/usr/bin/rsync&#8217;</span>
    </div>
    
    <div>
      <span>ITUNESSRC=&#8217;/Users/Shared/iTunes&#8217; # iTunes Folder</span>
    </div>
    
    <div>
      <span>ITUNESDST=&#8217;/Volumes/Volume_1/Catalog\ Backups/iTunes&#8217; #Destination for iTunes Backup</span>
    </div>
    
    <div>
      <span>IPHOTOSRC=&#8217;/Users/Shared/iPhoto&#8217; #iPhoto Folder</span>
    </div>
    
    <div>
      <span>IPHOTODST=&#8217;/Volumes/Volume_1/Catalog\ Backups/iPhoto&#8217; #Destination for iPhoto Backup</span>
    </div>
    
    <div>
      <span>PARAMS=&#8217;&#8211;ignore-existing &#8211;delete &#8211;progress &#8211;recursive &#8211;perms &#8211;times &#8211;size-only &#8211;whole-file&#8217; # Any parameters for rsync</span>
    </div>
    
    <div>
      <span>EXCLUDEITUNES=&#8217;-exclude=&#8217;.*&#8217; -exclude=&#8217;*.m4v&#8221; # Files or folders for exclusion</span>
    </div>
    
    <div>
      <span>EXCLUDEIPHOTO=&#8217;-exclude=&#8217;.*&#8221; # Files or folders for exclusion</span>
    </div>
    
    <div>
      <span><br /></span>
    </div>
    
    <div>
      <span>$RSYNC $PARAMS $EXCLUDEITUNES $ITUNESSRC $ITUNESDST</span>
    </div>
    
    <div>
      <span><br /></span>
    </div>
    
    <div>
      <span>$RSYNC $PARAMS $EXCLUDEIPHOTO $IPHOTOSRC $IPHOTODST</span>
    </div>
    
    <div>
      <span><br /></span>
    </div>
  </div>
  
  <div>
    <div>
      <span>Thats it. Since the &#8220;&#8211;delete&#8221; flag is in place, I recommend use of the &#8220;&#8211;dry-run&#8221; flag the first time to make sure it does what you want, since delete <b>will</b> remove everything in it&#8217;s path and make the folder match. I just have this run from cron every day using this line in my users crontab.</span>
    </div>
    
    <div style="font-size: small; ">
    </div>
    
    <div style="font-size: small; ">
    </div>
    
    <div>
      <div>
        <div>
          <span>@daily<span style="white-space: pre; "> </span>/opt/local/bin/rsynccatalogs.sh</span>
        </div>
      </div>
    </div>
    
    <div style="font-size: small; ">
    </div>
  </div>
  
  <div>
  </div>
</div>

<div>
  [[ This is a content summary only. Visit my website for full links, other content, and more! ]]
</div>