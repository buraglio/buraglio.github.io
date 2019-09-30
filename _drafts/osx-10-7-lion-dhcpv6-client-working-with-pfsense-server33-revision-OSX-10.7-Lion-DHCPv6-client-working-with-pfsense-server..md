---
id: 234
title: OSX (10.7; Lion) DHCPv6 client working with pfsense server.
date: 2011-07-26T12:20:00-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2011/07/33-revision/
permalink: /2011/07/33-revision/
---
It looks like MacOS 10.7 (Lion) has fully functioning DHCPv6. It&#8217;s about time.

Before:

[<img style="cursor:pointer; cursor:hand;width: 400px; height: 343px;" src="http://1.bp.blogspot.com/-6FQwzCiawpg/TjDWmwrbONI/AAAAAAAAAEI/9mOtP9fMbqE/s400/Screen%2BShot%2B2011-07-25%2Bat%2B8.45.24%2BPM.png" border="0" alt=""id="BLOGGER_PHOTO_ID_5634239095230904530" />](http://1.bp.blogspot.com/-6FQwzCiawpg/TjDWmwrbONI/AAAAAAAAAEI/9mOtP9fMbqE/s1600/Screen%2BShot%2B2011-07-25%2Bat%2B8.45.24%2BPM.png)

After:

[<img style="cursor:pointer; cursor:hand;width: 400px; height: 366px;" src="http://4.bp.blogspot.com/-stFnUb3g1zI/TjDW1MDpOyI/AAAAAAAAAEY/YgG7fXCfujY/s400/Screen%2BShot%2B2011-07-26%2Bat%2B7.18.45%2BAM.png" border="0" alt=""id="BLOGGER_PHOTO_ID_5634239343098411810" />](http://4.bp.blogspot.com/-stFnUb3g1zI/TjDW1MDpOyI/AAAAAAAAAEY/YgG7fXCfujY/s1600/Screen%2BShot%2B2011-07-26%2Bat%2B7.18.45%2BAM.png)

pfSense setup:

[<img style="cursor:pointer; cursor:hand;width: 400px; height: 341px;" src="http://2.bp.blogspot.com/-gSN5Rx7vIUU/TjDW0t1BcEI/AAAAAAAAAEQ/1hQNIlCJl30/s400/Screen%2BShot%2B2011-07-26%2Bat%2B7.16.50%2BAM.png" border="0" alt=""id="BLOGGER_PHOTO_ID_5634239334984020034" />](http://2.bp.blogspot.com/-gSN5Rx7vIUU/TjDW0t1BcEI/AAAAAAAAAEQ/1hQNIlCJl30/s1600/Screen%2BShot%2B2011-07-26%2Bat%2B7.16.50%2BAM.png)

Using Internet Systems Consortium DHCP Server 4.2.1-P1 as the server (on my pfSense box) I am able to get not only a privacy address (via stateless autoconfigure) but also a normal EUI-64 address as well as an IPv6 address via dhcpv6. 

<div>
</div>

<div>
  I didn&#8217;t do anything except use the &#8220;Automatic&#8221; setting in the network control panel, so out of the box OSX 10.7 &#8220;Lion&#8221; looks like it does the right thing with DHCPv6, at least at face value.</p> 
  
  <div>
    <div>
      <span><span style="white-space: pre;"><br /></span></span>
    </div>
    
    <div>
    </div>
    
    <p>
      </div> </div> 
      
      <div>
        [[ This is a content summary only. Visit my website for full links, other content, and more! ]]
      </div>