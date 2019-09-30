---
id: 1000
title: 'NIX4NetEng #1 Managing dotfiles; pwn the unspoken pain of UNIX administration'
date: 2014-04-30T20:58:20-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2014/04/994-revision-v1/
permalink: /2014/04/994-revision-v1/
---
Many network engineers are also tasked with maintaining systems that provide network services, those things that make the network easier to use such as DNS and DHCP or management systems that perform useful things like monitor the network, collect flow data or bestow access to the equipment by acting as <a href="http://en.wikipedia.org/wiki/Bastion_host" target="_blank">bastion</a> or jump hosts.  In many instances, robust and high availability services run on UNIX, Linux or BSD systems for stability and reliability, so those that manage these systems need to be well versed system admins as well as whatever their other job functions are.  <a href="http://packetpushers.net/are-certifications-tests-still-worth-your-resources-in-the-day-of-hybrid-it/" target="_blank">Hybridization</a>, if you will.  Nothing new, nothing unexpected.  However, one of the banes of these tasks is having a uniform shell environment across platforms and systems. Why create a customized environment with aliases, environmental variables and other personalized settings more than once?

I have struggled with how to do this efficiently across desktop, server, jumphosts and other daily use systems for **years**. Most of the important variables are controlled by dotfiles.   In what I am hoping is the start of a short series of &#8220;UNIX stuff for networking folks&#8221;, I will explain how I did this for myself.

UNIX and Linux admins have been dealing with dotfiles forever. GitHub even has a <a href="http://dotfiles.github.io/" target="_blank">repo dedicated to</a> it.  For my environment, I chose to go with <a href="http://jim.github.io/briefcase/" target="_blank">Briefcase</a> and <a href="http://www.bitbucket.com" target="_blank">BitBucket</a>.  Briefcase because it has mechanisms for stripping out sensitive information if needed and bitbucket because I can have private repos without paying money.  This can all certainly be done with local git repos or github and without briefcase.

Briefcase is really straightforward to install, it&#8217;s just a ruby gem, so _gem install briefcase_ is all that is needed to get it on your machine_._  OSX has it by default.  _ _On my machine I needed to to_ sudo gem update —system_ before it would install.  Your mileage may vary_. _

Once it&#8217;s installed, just add your files.  I switched to bash, so I needed to import .bashrc and .bash_profile, but I wanted to make sure I had a backup just in case.

<pre>mkdir -p tmp/dotfiles
mv .bashrc tmp/dotfiles/
mv .bash_profile tmp/dotfiles/</pre>

<pre>briefcase import ~/.bashrc
briefcase import ~/.bash_profile</pre>

<pre>briefcase git remote add origin git@repo.forwardingplane.net:buraglio/briefcase-dotfiles.git</pre>

<pre>briefcase git commit -am "Initial newhost commit"</pre>

<pre>briefcase git checkout origin master</pre>

Obviously replace the remote repo address with your own repo destination.   You can now check the status:

<pre>briefcase sync</pre>

This should output something like this:

<pre>Synchronizing dotfiles between /Users/buraglio/.dotfiles and /Users/buraglio
Symlink verified: /Users/buraglio/.bash_profile -&gt; /Users/buraglio/.dotfiles/bash_profile
Symlink verified: /Users/buraglio/.bashrc -&gt; /Users/buraglio/.dotfiles/bashrc
Symlink verified: /Users/buraglio/.profile -&gt; /Users/buraglio/.dotfiles/profile
Symlink verified: /Users/buraglio/.README.md -&gt; /Users/buraglio/.dotfiles/README.md</pre>

Getting a new branch for an existing host was the biggest hurdle for me, I want a base .bashrc but may want different environment variables for mac and Linux.  I&#8217;m not a git expert by any means, so there may be a better way to do this, but it works well for me. To branch a new host, it&#8217;s pretty straightforward.  Briefcase is really just a wrapper for git, so prepending &#8220;briefcase&#8221; before the git commands seems to &#8220;just work&#8221; (as I learned by trial and error or making this work).

On an existing Host:

<pre>git clone git@your.repoaddress.net:username/reponame.git .dotfiles
mkdir -p tmp/dotfiles
mv .bashrc tmp/dotfiles/
mv .bash_profile tmp/dotfiles/
briefcase sync
briefcase git branch [newhost]
briefcase git checkout [newhost]</pre>

&#8230;Make changes&#8230;

<pre>briefcase git commit -am "Initial newhost commit"</pre>

briefcase git push origin [newhost]

There you have it, easily backed up and distributed environment control.  I&#8217;m planning to add <a href="http://joeyh.name/code/etckeeper/" target="_blank">etckeeper</a> to this process next.