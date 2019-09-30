---
id: 1333
title: Building Interdomain SDN part 3
date: 2015-11-05T22:37:23-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2015/11/1330-revision-v1/
permalink: /2015/11/1330-revision-v1/
---
A few years ago I wrote [some text](http://www.forwardingplane.net/2012/11/sdn-across-domains-in-the-wan-a-novice-look/) on [interdomain SDN](http://www.forwardingplane.net/2013/01/sdn-across-the-wan-part-deux-primitives/). Years later, work is being done, smart people are thinking about it and building ways to make it a reality. Not being one to give up on an idea, I gave [this presentation](https://docs.google.com/presentation/d/1anAaqWR8wmzKO5fqidDy9QJXW4RiVshX9Miq3PoDv9E/edit) in may at [ChiNOG](http://chinog.org/meetings/chi-nog-05/)  on what my take on what that architecture should be. I (we) propose that the use of existing protocols such as [BGP FlowSpec](https://tools.ietf.org/html/rfc5575) will make this realistically deployable and maintainable given some [simple, pluggable middleware](https://github.com/dwcarder/sdn-ix-demo). As work continues to happen on this, my belief is that this is a very sound (and simple) concept. The middleware is modular and flexible enough that it can stand alone or plug into an existing code base such as ODL or Ryu. As <a href="http://sc15blog.blogspot.com/2015/11/simplifying-worlds-most-powerful.html" target="_blank">I work on the SDN deployment</a> for the [annual international supercomputing conference](http://www.sc15.org), and work on the [SDN for scientific networking workshop](https://www.es.net/network-r-and-d/workshops/),  I become more and more convinced that there needs to be an operationally viable and simple way to support these types of networks in ways that are thin and simple since it is a newer concept and some of the protocols involved (e.g. OpenFlow) is still in its infancy.  Here is the video of the talk for anyone interested in listening to me talk about it for 20 minutes.



As a reference, this is a great talk from the same conference on BGP FlowSpec that adds a lot of credence to the use of it as a policy dissemination protocol.