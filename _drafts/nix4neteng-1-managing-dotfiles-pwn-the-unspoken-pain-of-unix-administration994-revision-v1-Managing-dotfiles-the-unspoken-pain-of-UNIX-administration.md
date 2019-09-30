---
id: 995
title: Managing dotfiles; the unspoken pain of UNIX administration
date: 2014-04-26T09:08:35-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2014/04/994-revision-v1/
permalink: /2014/04/994-revision-v1/
---
Many network engineers are also tasked with maintaining systems that provide network services, those things that make the network easier to use such as DNS and DHCP or management systems that perform useful things like monitor the network, collect flow data or bestow access to the equipment by acting as <a href="http://en.wikipedia.org/wiki/Bastion_host" target="_blank">bastion</a> or jump hosts.  In many instances, robust and high availability services run on UNIX, Linux or BSD systems for stability and reliability, so those that manage these systems need to be well versed system admins as well as whatever their other job functions are.  <a href="http://packetpushers.net/are-certifications-tests-still-worth-your-resources-in-the-day-of-hybrid-it/" target="_blank">Hybridization</a>, if you will.  Nothing new, nothing unexpected.  However, one of the banes of these tasks is the shell environment.  Most of the important variables are controlled by dotfiles.

UNIX admins have been dealing with dotfiles forever.

http://dotfiles.github.io/

<span style="text-decoration: underline;">http://jim.github.io/briefcase/</span>

briefcase git status  
briefcase git remote add origin git@repo.forwardingplane.net:buraglio/briefcase-dotfiles.git  
briefcase git checkout origin master  
briefcase git branch [newhost] origin/master

&nbsp;

Existing Host:

git clone git@your.repoaddress.net:username/reponame.git .dotfiles

mkdir -p tmp/dotfiles

mv .bashrc tmp/dotfiles/

mv .bash_profile tmp/dotfiles/

briefcase sync

briefcase git branch newhost

briefcase git checkout newhost

&#8230;Make changes&#8230;

briefcase git commit -am &#8220;Initial newhost commit&#8221;

briefcase git push origin newhost