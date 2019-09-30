---
id: 1019
title: 'NIX4NetEng #2 IPv4/6 address investigation tools'
date: 2014-05-31T11:16:39-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2014/05/1018-revision-v1/
permalink: /2014/05/1018-revision-v1/
---
I don&#8217;t care what your vendor alignment of choice is, Cisco, Juniper, Brocade, Alcatel&#8230;.it doesn&#8217;t matter. At one point or another you&#8217;re going to need to bird dog an address to see where it&#8217;s coming from, who owns it, what it&#8217;s DNS name is or what path you&#8217;re taking to get to it.  This is an intersting one, as address management and lookups  can bleed into other aspects of networking like path selection, latency, jitter and many other things.  I&#8217;m going to touch on a few things and give generalizations on a few others.  First, quering where things originate and who has ownership is infinitely useful, especially if your job description has &#8220;security&#8221; anywhere in it, written or implied.  I like to use a range of services, all of which are from the CLI (for speed and scriptability).  My go-to tool for this is the venerable <a href="http://en.wikipedia.org/wiki/Whois" target="_blank">whois</a> tool.

Lets say I want to check on the address 192.80.96.88.

First, lets figure out if it&#8217;s got a name.  dig is your friend here.

<pre>(~) tardis $ dig -x 192.80.96.88</pre>

; <<>> DiG 9.8.3-P1 <<>> -x 192.80.96.88  
;; global options: +cmd  
;; Got answer:  
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 29443  
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0  
;; QUESTION SECTION:  
;88.96.80.192.in-addr.arpa. IN PTR  
;; ANSWER SECTION:  
88.96.80.192.in-addr.arpa. 7145 IN PTR local.forwardingplane.net.  
;; Query time: 2 msec  
;; SERVER: 10.209.209.1#53(10.209.209.1)  
;; WHEN: Sat May 31 11:43:18 2014  
;; MSG SIZE rcvd: 82

Dig is an incredibly powerful DNS tool. I&#8217;d recommend learning it as well as you possibly can. _man dig_ on any good unix box should give you a good start, <a href="http://www.thegeekstuff.com/2012/02/dig-command-examples/" target="_blank">this site</a> has some good examples too.  Here we see that the address has reverse DNS (PTR record) of local.forwardingplane.net.  We can poke a bit more at this using DNS, too.

<pre>(~) tardis $ dig -t ANY local.forwardingplane.net +noall +answer

; &lt;&lt;&gt;&gt; DiG 9.8.3-P1 &lt;&lt;&gt;&gt; -t ANY local.forwardingplane.net +noall +answer
;; global options: +cmd
local.forwardingplane.net. 221 IN AAAA 2607:dd00:8000:18::88
local.forwardingplane.net. 221 IN A 192.80.96.88</pre>

Well, we can see here we have a dual stacked host.  We&#8217;ll look at that more later.

Let&#8217;s see who owns this address space. Whois is the way to go here.  I always start with querying ARIN and go from there.

&nbsp;

<pre>(~) tardis-3 $ whois -h whois.arin.net 192.80.96.88

#
# ARIN WHOIS data and services are subject to the Terms of Use
# available at: https://www.arin.net/whois_tou.html
#

#
# Query terms are ambiguous.  The query is assumed to be:
#     "n 192.80.96.88"
#
# Use "?" to get help.
#

#
# The following results may also be obtained via:
# http://whois.arin.net/rest/nets;q=192.80.96.88?showDetails=true&showARIN=false&ext=netref2
#

NetRange:       192.80.96.0 - 192.80.111.255
CIDR:           192.80.96.0/20
OriginAS:       AS10932
NetName:        UC2B-1
NetHandle:      NET-192-80-96-0-1
Parent:         NET-192-0-0-0-0
NetType:        Direct Allocation
RegDate:        2013-02-27
Updated:        2013-02-27
Ref:            http://whois.arin.net/rest/net/NET-192-80-96-0-1

OrgName:        UC2B
OrgId:          CCLAUBBC
Address:        102 North Neil Street
City:           Champaign
StateProv:      IL
PostalCode:     61820
Country:        US
RegDate:        2012-02-28
Updated:        2014-02-19
Ref:            http://whois.arin.net/rest/org/CCLAUBBC

OrgAbuseHandle: UCBTE-ARIN
OrgAbuseName:   uc2b-tech
OrgAbusePhone:  +1-217-265-4226
OrgAbuseEmail:  uc2b-tech@uc2b.net
OrgAbuseRef:    http://whois.arin.net/rest/poc/UCBTE-ARIN

OrgNOCHandle: UCBTE-ARIN
OrgNOCName:   uc2b-tech
OrgNOCPhone:  +1-217-265-4226
OrgNOCEmail:  uc2b-tech@uc2b.net
OrgNOCRef:    http://whois.arin.net/rest/poc/UCBTE-ARIN

OrgTechHandle: UCBTE-ARIN
OrgTechName:   uc2b-tech
OrgTechPhone:  +1-217-265-4226
OrgTechEmail:  uc2b-tech@uc2b.net
OrgTechRef:    http://whois.arin.net/rest/poc/UCBTE-ARIN

#
# ARIN WHOIS data and services are subject to the Terms of Use
# available at: https://www.arin.net/whois_tou.html
#</pre>

The first 7 lines of this are the most important.  
Here we can see that the address space is owned by an entity called UC2B, it is part of a /20 that the origin ASN is 10932 and that it is a direct allocation (as opposed to assigned space from an upstream provider).

<pre>NetRange:       192.80.96.0 - 192.80.111.255
CIDR:           192.80.96.0/20
OriginAS:       AS10932
NetName:        UC2B-1
NetHandle:      NET-192-80-96-0-1
Parent:         NET-192-0-0-0-0
NetType:        Direct Allocation</pre>

From here we can query the ASN, also using whois, again, the first few lines are generally the most useful.

<pre>(~) tardis $ whois -h whois.arin.net 10932
</pre>

<a href="http://www.team-cymru.org/Services/ip-to-asn.html#whois" target="_blank">Team Cymru has an extremely powerful whois service</a> that allows for significantly more flexibility including time and date.

<pre>(~) tardis $ whois -h whois.cymru.com " -v 192.80.96.88"
AS      | IP               | BGP Prefix          | CC | Registry | Allocated  | AS Name
10932   | 192.80.96.88     | 192.80.96.0/20      | US | arin     | 2013-02-27 | UC2B - UC2B,US</pre>