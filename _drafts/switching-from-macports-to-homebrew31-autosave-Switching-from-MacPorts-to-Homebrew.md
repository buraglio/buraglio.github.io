---
id: 207
title: Switching from MacPorts to Homebrew
date: 2012-12-13T15:09:31-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2012/12/31-autosave/
permalink: /2012/12/31-autosave/
---
<div>
  I&#8217;ve recently decided that even though I love the BSD style <a href="http://www.macports.org">MacPorts</a> system, it can be too clunky to maintain and doesn&#8217;t handle dependancies as well as I&#8217;d like (much like the actual BSD ports collection). So, in doing a little looking I found that <a href="http://www.finkproject.org/">Fink</a> is still out of date, but <a href="http://mxcl.github.com/homebrew/">Homebrew</a> is very simple and also really elegant comparatively speaking.
</div>

<div>
</div>

<div>
  Since homebrew doesn&#8217;t wrk well with other packge systems installed, and I already
</div>

<div>
</div>

<div>
  I&#8217;d like to know what I had installed since this system has been in use for 2+ years, so I do a list and send it to a txt file:
</div>

<div>
</div>

<div>
  <em>touch ~/Documents/installed.macports.txt</em>
</div>

<div>
  <em>sudo port list installed > Documents/installed.macports.txt</em>
</div>

<div>
  <div>
    <em>sudo cat .macports/history >> ~/Documents/installed.macports.txt</em>
  </div>
</div>

<div>
</div>

<div>
  Then I remove the installed packages:
</div>

<div>
</div>

<div>
  <em>sudo port -f uninstall installed</em>
</div>

<div>
</div>

<div>
  Per the instructions found on the <a href="http://guide.macports.org/chunked/installing.macports.uninstalling.html">MacPorts page</a>, remove all of the directories as such:
</div>

<div>
</div>

<div>
  <div>
    <em>sudo rm -rf \</em>
  </div>
  
  <div>
    <em> /opt/local \</em>
  </div>
  
  <div>
    <em> /Applications/DarwinPorts \</em>
  </div>
  
  <div>
    <em> /Applications/MacPorts \</em>
  </div>
  
  <div>
    <em> /Library/LaunchDaemons/org.macports.* \</em>
  </div>
  
  <div>
    <em> /Library/Receipts/DarwinPorts*.pkg \</em>
  </div>
  
  <div>
    <em> /Library/Receipts/MacPorts*.pkg \</em>
  </div>
  
  <div>
    <em> /Library/StartupItems/DarwinPortsStartup \</em>
  </div>
  
  <div>
    <em> /Library/Tcl/darwinports1.0 \</em>
  </div>
  
  <div>
    <em> /Library/Tcl/macports1.0 \</em>
  </div>
  
  <div>
    <em> ~/.macports</em>
  </div>
</div>

<div>
</div>

<div>
  If this is an upgraded machine (say, from 10.6 to 10.7), you&#8217;ll need to also reinstall the Xcode Developer Tools via the app store before installing homebrew.
</div>

<div>
</div>

<div>
  After waiting forever to get XCode downloaded, and since it&#8217;s been installed via the App Store under Lion (10.7), I need to run the “Install Xcode” app that is placed in /Applications.
</div>

<div>
</div>

<div>
  Now I can <a href="https://github.com/mxcl/homebrew/wiki/Installation">Install homebrew</a> via the handy cli command:
</div>

<div>
</div>

<div>
  <em>sudo /usr/bin/ruby -e &#8220;$(curl -fsSL https://raw.github.com/gist/323731)&#8221;</em>
</div>

<div>
  <em><br /> </em>
</div>

<div>
  You&#8217;ll then see something like this:
</div>

<div>
</div>

<div>
  <div>
    <em>==> This script will install:</em>
  </div>
  
  <div>
    <em>/usr/local/bin/brew</em>
  </div>
  
  <div>
    <em>/usr/local/Library/Formula/&#8230;</em>
  </div>
  
  <div>
    <em>/usr/local/Library/Homebrew/&#8230;</em>
  </div>
  
  <div>
    <em>==> The following directories will be made group writable:</em>
  </div>
  
  <div>
    <em>/usr/local/share/man</em>
  </div>
  
  <div>
    <em>/usr/local/lib/pkgconfig</em>
  </div>
  
  <div>
    <em>/usr/local/share/man/man8</em>
  </div>
  
  <div>
    <em>/usr/local/share/doc</em>
  </div>
  
  <div>
    <em>/usr/local/bin</em>
  </div>
  
  <div>
    <em>/usr/local/include</em>
  </div>
  
  <div>
    <em>/usr/local/lib</em>
  </div>
  
  <div>
    <em>/usr/local/share</em>
  </div>
  
  <div>
    <em>==> The following directories will have their group set to staff:</em>
  </div>
  
  <div>
    <em>/usr/local/share/man</em>
  </div>
  
  <div>
    <em>/usr/local/lib/pkgconfig</em>
  </div>
  
  <div>
    <em>/usr/local/share/man/man8</em>
  </div>
  
  <div>
    <em>/usr/local/share/doc</em>
  </div>
  
  <div>
    <em>/usr/local/bin</em>
  </div>
  
  <div>
    <em>/usr/local/include</em>
  </div>
  
  <div>
    <em>/usr/local/lib</em>
  </div>
  
  <div>
    <em>/usr/local/share</em>
  </div>
  
  <div>
    <em><br /> </em>
  </div>
  
  <div>
    <em>Press enter to continue</em>
  </div>
</div>

<div>
  <em><br /> </em>
</div>

<div>
  If you want to continue, hit enter.<em> </em> In my case, I saw this:
</div>

<div>
  <em><br /> </em>
</div>

<div>
  <div style="font-style: italic;">
    ==> /usr/bin/sudo /bin/chmod o+w /usr/local
  </div>
  
  <div style="font-style: italic;">
    ==> /usr/bin/sudo /bin/chmod g+w /usr/local/share/man /usr/local/lib/pkgconfig /usr/local/share/man/man8 /usr/local/share/doc /usr/local/bin /usr/local/include /usr/local/lib /usr/local/share
  </div>
  
  <div style="font-style: italic;">
    ==> /usr/bin/sudo /usr/bin/chgrp staff /usr/local/share/man /usr/local/lib/pkgconfig /usr/local/share/man/man8 /usr/local/share/doc /usr/local/bin /usr/local/include /usr/local/lib /usr/local/share
  </div>
  
  <div style="font-style: italic;">
    ==> Downloading and Installing Homebrew&#8230;
  </div>
  
  <div style="font-style: italic;">
    ==> /usr/bin/sudo /bin/chmod o-w /usr/local
  </div>
  
  <div style="font-style: italic;">
    Warning: Now install Xcode: http://developer.apple.com/technologies/xcode.html
  </div>
  
  <div style="font-style: italic;">
    Warning: The following *evil* dylibs exist in /usr/local/lib
  </div>
  
  <div style="font-style: italic;">
    They may break builds or worse. You should consider deleting them:
  </div>
  
  <div style="font-style: italic;">
    /usr/local/lib/libfuse.2.dylib
  </div>
  
  <div style="font-style: italic;">
    /usr/local/lib/libfuse_ino64.2.dylib
  </div>
  
  <div style="font-style: italic;">
    ==> Installation successful!
  </div>
  
  <div style="font-style: italic;">
    Now type: brew help
  </div>
  
  <div style="font-style: italic;">
  </div>
  
  <div>
    I chose to leave those libraries and deal with the fallout as I saw it.
  </div>
</div>

<div>
</div>

<div>
  Now I need to install the base repository manager that brew uses:
</div>

<div>
</div>

<div>
  <em>sudo brew install git</em>
</div>

<div>
</div>

<div>
  Then I can update the brew repository:
</div>

<div>
</div>

<div>
  <em>sudo brew update</em>
</div>

<div>
  <em><br /> </em>
</div>

<div>
  That&#8217;s basically it. Now I can install apps via HomeBrew using the simple command:
</div>

<div>
</div>

<div>
  <em>sudo brew install </em>
</div>

<div>
</div>

<div>
  I chose to install nmap as a test:
</div>

<div>
</div>

<div>
  <em>sudo brew install nmap</em>
</div>

<div>
  <em><br /> </em>
</div>

<div>
  You&#8217;re done. Enjoy your HomeBrew =)
</div>

<div>
</div>

<div>
</div>

<div>
</div>

<div>
</div>

<div>
  [[ This is a content summary only. Visit my website for full links, other content, and more! ]]
</div>