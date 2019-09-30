---
id: 1099
title: OpenVswitch 2.3.0 RPMs
date: 2014-10-09T16:08:25-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2014/10/1098-revision-v1/
permalink: /2014/10/1098-revision-v1/
---
I was wanting to do a few quick mock-ups with <a href="http://openvswitch.org/" target="_blank">OpenvSwitch</a> and <a href="http://www.opendaylight.org/" target="_blank">OpenDayLight</a> and wanted to use CentOS since I have templates for it that I replicate.  Just like with the <a title="OpenvSwitch 2.0 Debian packages" href="http://www.forwardingplane.net/2013/11/openvswitch-2-0-debian-packages/" target="_blank">debian stuff I had been doing</a>, I wasn&#8217;t able to find any in some quick searches.   I stumbled upon <a href="http://n40lab.wordpress.com/2014/09/04/openvswitch-2-3-0-lts-and-centos-7/" target="_blank">This site</a>, which had a great how to for building them, so I just used that.  Seeing as that the debian packages actually got downloaded a lot, I figured I&#8217;d post these RPMs as well.  They&#8217;re available <a href="http://www.forwardingplane.net/wp-content/uploads/OVS2.0/OpenvSwitch-2.3.0-RPM.tgz" target="_blank">here</a> and should work on CentOS 6.5 and probably 7.

Just do a quick local install and start the service and you should be up and running.

&nbsp;

<pre>yum localinstall /home/ovswitch/rpmbuild/RPMS/x86_64/openvswitch-2.3.0-1.x86_64.rpm 
sudo service openvswitch start</pre>

<pre></pre>