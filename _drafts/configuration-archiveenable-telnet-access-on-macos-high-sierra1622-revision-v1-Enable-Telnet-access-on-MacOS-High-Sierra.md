---
id: 1625
title: Enable Telnet access on MacOS High Sierra
date: 2019-03-02T10:14:03-06:00
author: Nick Buraglio
layout: revision
guid: https://www.forwardingplane.net/2019/03/1622-revision-v1/
permalink: /2019/03/1622-revision-v1/
---
Lots of things changed under the hood in MacOS high sierra. One of those was to enable a sandbox like environment and to remove insecure communication protocols. This breaks things like console communication to the network modeling and virtualization platform [Eve-NG](https://www.eve-ng.net/). It&#8217;s fairly trivial to re-enable it, however. This can be accomplished by doing the following steps. 

Install [Homebrew](http://www.homebrew.sh). Open your favorite terminal application (I like to use [iTerm2](https://www.iterm2.com/) (also installable via homebrew), but Terminal works fine.) 

<pre class="wp-block-preformatted">1. Reboot your Mac and hold the CMD + R keys <br />2. When presented with the recovery options, click Utilities at the top and choose Terminal <br />3. Type; csrutil disable <br />4. Reboot as normal <br />6. terminal and type; <br />brew install telnet <br />sudo ln -s /usr/local/bin/telnet /usr/bin/telnet <br />7. Again, Reboot your Mac and hold the CMD + R keys <br />8. When presented with the recovery options, click Utilities at the top and choose Terminal <br />9. Type; csrutil enable <br />10. Reboot as normal </pre>

You&#8217;re done. You can have telnet for your internal communication to Eve-NG consoles. **Don&#8217;t use it to talk to production network gear, because it&#8217;s not 1998.**