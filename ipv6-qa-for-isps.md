---
id: 1537
title: 'IPv6 Q&#038;A for ISPs'
date: 2018-12-14T19:33:13-06:00
author: Nick Buraglio
layout: page
guid: https://www.forwardingplane.net/?page_id=1537
image: /wp-content/uploads/2018/12/go_ipv6_blog_banner-01-02-1.png
---
<img style="display: block; margin-left: auto; margin-right: auto;" title="go_ipv6_blog_banner-01-02.png" src="https://www.forwardingplane.net/wp-content/uploads/2018/12/go_ipv6_blog_banner-01-02-2.png" alt="Go ipv6 blog banner 01 02" width="555" height="203" border="0" />

As a follow on to my post on [why small to medium ISPs should deploy IPv6](https://www.forwardingplane.net/2018/09/as-a-small-to-medium-isp-why-you-should-deploy-ipv6/) and the associated [APNIC blog post,](https://blog.apnic.net/2018/12/13/three-reasons-why-ipv6-is-worth-the-effort/) I have begun to compile a list of commonly asked questions IPv6 and their answers in relation to how a small to medium sized ISP can (and should) deploy IPv6. Expect this list to change and grow over time.

&#8212;&#8212;

**Q: As a small to medium sized ISP, how much IPv6 address space do I need?**

**&#8212;&#8212;-**

A: This is heavily dependent on your environment and your RIR policy. Most will allocate a /36 or a /32. Either one is likely more than you will need, and my advice is typically to get the /32 and then create a solid address plan that accounts for future growth.Remember, subnetting should be done on the nibile boundary. If possible, try not to let cost drive technical decisions in this space. Best current practice for address allocation can be found [here](https://getipv6.info/display/IPv6/IPv6+Address+Allocation+BCP).

&#8212;&#8212;  
**Q: Is there DHCP in IPv6? **  
&#8212;&#8212;

A:  There are [multiple DHCPv6 implementations](https://en.wikipedia.org/wiki/DHCPv6), the one I like to use is isc-dhcpd as it tends to have the best standard support, is incredibly feature rich and well documented and is very scalable, but there are multiple options. Examples can be found in the [configuration archive](https://www.forwardingplane.net/configuration-archive/) [here](https://www.forwardingplane.net/configuration-archive/dhcp-and-dhcpv6-relay/).  
&#8212;&#8212;-  
**Q: How does one know what IP address the CPE has?**  
&#8212;&#8212;  
A: DUID (DHCP Unique Identifier), PPPoE, etc. There are several ways.  
&#8212;&#8212;-  
**Q: How does one perform traffic shaping for the entire /64 (or /48, or other nibble boundary block) assigned to the customer?**  
&#8212;&#8212;  
A: Don’t shape on L3, it doesn’t scale. Shape on L2 at the CPE or use PPPoE.  
&#8212;&#8212;  
**Q) Can a dynamic CPE environment where devices can pull addresses with minimal input and work from the provider still work?**  
&#8212;&#8212;  
A: Yes, DHCPv6 and [DHCPv6-PD](https://en.wikipedia.org/wiki/Prefix_delegation) handle these functions. There are well traveled and well vetted how-to’s for this. It is how the large incumbent providers work, regardless of delivery last mile (DSL, DOCSIS, Fixed wireless, etc.)

&#8212;&#8212;-  
**Q: How does the host configure a host address? **  
&#8212;&#8212;-

A: Most devices will use what is called SLAAC. Addresses are auto-generated based on a MAC. A given host will have multiple IPv6 addresses and this is normal. There will also be the following on a HOST:  
A link local address on every interface (starts with fe80: and is used for any communication on the same L2 segment)  
A privacy address that rotates which much of the traffic will be worked from  
An EUI-64 address (the auto configured address)  
Potentially, but only when configured:  
A DHCPv6 assigned address.  
A Static Address

On the ISP side, you’ll see any or all of the following:  
A link local address (starts with fe80:)  
An EUI-64 address  
A static address  
A prefix delegated prefix

**———**  
Other commonly questions and advice

**How should I lay out my new IPv6 address space? **

Like most things in networking, the answer is “it depends”. It needs to work for your environment and workflow. There really is no truly “wrong” way, but there are some ways that are certainly better simply due to hierarchy and management. One of the most common mistakes it to jump in without at least a rough plan. I learned this the hard way oh-so-long-ago.  Below are a few of the little spoken of tidbits that I learned the hard way or was taught by someone who learned through mistakes.

Come up with a reasonable IPv6 address plan before you start &#8211; work through it as you can. Start with your backbone  
You will no longer memorize addresses (which you should not do anyway), instead, do two things:

Think of all prefixes like you would consider a unique IPv4 address 4.2.2.2/32 ==2001:db8:44:22::/64  
IPv6 addresses are written with the CIDR prefix (see above). A good write up and straw-man address plan can be found on [John Osmon](https://www.linkedin.com/in/john-osmon-2a5a421/)’s site [here](http://www.miscreantsinaction.com/2018/12/joes-internet-goes-ipv6-adventure-in_18.html).

Use DNS for everything you can &#8211; an IPAM like NetBox is your friend  
It’s ok if your customers prefix delegation does not have reverse DNS  
It’s ok to publicly address your infrastructure with IPv6. Use a single /48 dedicated for all infrastructure and then create an ACL at the network border to limit access  
Public addresses for your customers are ok.  
There is no NAT as in the IPv4 world, and there should not be NAT for IPv6. Period.  
Yes, you want to dual-stack. It’s ok to have RFC1918 space plus public IPv6. In fact, that’s the most prevalent model (look at your cell phone)  
You will have devices that won’t do IPv6. That’s expected.  
Yes, you can do IPv6 only, but it’s significantly harder to manage than a standard dual stack network.

* Image source APNIC Blog

<div class="sharedaddy sd-sharing-enabled">
  <div class="robots-nocontent sd-block sd-social sd-social-icon-text sd-sharing">
    <h3 class="sd-title">
      Share this:
    </h3>
    
    <div class="sd-content">
      <ul>
        <li class="share-twitter">
          <a rel="nofollow noopener noreferrer" data-shared="sharing-twitter-1537" class="share-twitter sd-button share-icon" href="http://www.forwardingplane.net/ipv6-qa-for-isps/?share=twitter" target="_blank" title="Click to share on Twitter"><span>Twitter</span></a>
        </li>
        <li class="share-email">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-email sd-button share-icon" href="http://www.forwardingplane.net/ipv6-qa-for-isps/?share=email" target="_blank" title="Click to email this to a friend"><span>Email</span></a>
        </li>
        <li class="share-print">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-print sd-button share-icon" href="http://www.forwardingplane.net/ipv6-qa-for-isps/" target="_blank" title="Click to print"><span>Print</span></a>
        </li>
        <li class="share-linkedin">
          <a rel="nofollow noopener noreferrer" data-shared="sharing-linkedin-1537" class="share-linkedin sd-button share-icon" href="http://www.forwardingplane.net/ipv6-qa-for-isps/?share=linkedin" target="_blank" title="Click to share on LinkedIn"><span>LinkedIn</span></a>
        </li>
        <li class="share-facebook">
          <a rel="nofollow noopener noreferrer" data-shared="sharing-facebook-1537" class="share-facebook sd-button share-icon" href="http://www.forwardingplane.net/ipv6-qa-for-isps/?share=facebook" target="_blank" title="Click to share on Facebook"><span>Facebook</span></a>
        </li>
        <li class="share-reddit">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-reddit sd-button share-icon" href="http://www.forwardingplane.net/ipv6-qa-for-isps/?share=reddit" target="_blank" title="Click to share on Reddit"><span>Reddit</span></a>
        </li>
        <li class="share-tumblr">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-tumblr sd-button share-icon" href="http://www.forwardingplane.net/ipv6-qa-for-isps/?share=tumblr" target="_blank" title="Click to share on Tumblr"><span>Tumblr</span></a>
        </li>
        <li class="share-pinterest">
          <a rel="nofollow noopener noreferrer" data-shared="sharing-pinterest-1537" class="share-pinterest sd-button share-icon" href="http://www.forwardingplane.net/ipv6-qa-for-isps/?share=pinterest" target="_blank" title="Click to share on Pinterest"><span>Pinterest</span></a>
        </li>
        <li class="share-pocket">
          <a rel="nofollow noopener noreferrer" data-shared="" class="share-pocket sd-button share-icon" href="http://www.forwardingplane.net/ipv6-qa-for-isps/?share=pocket" target="_blank" title="Click to share on Pocket"><span>Pocket</span></a>
        </li>
        <li class="share-end">
        </li>
      </ul>
    </div>
  </div>
</div>