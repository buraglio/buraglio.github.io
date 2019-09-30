---
id: 631
title: Scripting the build of OpenDayight Controller under CentOS
date: 2013-05-03T12:35:57-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2013/05/627-revision-4/
permalink: /2013/05/627-revision-4/
---
<a href="https://twitter.com/blinken_lichten" target="_blank">Jon Langemak</a> has a great write up on <a href="http://www.dasblinkenlichten.com/installing-opendaylight-on-centos/" target="_blank">building the OpenDaylight controller under CentOS</a>. Since I&#8217;ll have to do this a bunch of times, I though tI&#8217;d take what he so generously put online and build a very rudimentary script for deploying ODC under CentOS. The prerequisites are that you already have an account and ssh key at the <a href="https://git.opendaylight.org/" target="_blank">OpenDaylight GIT repo</a> and that you <a href="http://www.revsys.com/writings/quicktips/turn-off-selinux.html" target="_blank">disable SELinux</a>.

Here is the script:

#!/bin/bash

\# Install Opendaylight controller under CentOS  
\# by nick [at] buraglio.com http://www.twitter.com/buraglio  
\# http://www.forwardingplane.net  
\# Based on post by Jon Langemak (http://www.twitter.com/blinken_lichten  
\# http://www.dasblinkenlichten.com/installing-opendaylight-on-centos/

yum=&#8221;/usr/bin/yum&#8221;  
servivce=&#8221;/sbin/service&#8221;  
chkconfig=&#8221;/sbin/chkconfig&#8221;

echo &#8220;\***\***\***\***\***\***\***\***&#8221;  
echo &#8220;\***\***\***\***\***\***\***\***&#8221;  
echo &#8220;Disable SELINUX before starting this process&#8221;  
echo &#8220;Edit the /etc/selinux/config file and restart the server&#8221;  
echo &#8220;\***\***\***\***\***\***\***\***&#8221;  
echo &#8220;\***\***\***\***\***\***\***\***&#8221;  
echo &#8220;Change the username in the GIT section to your own&#8221;  
echo &#8220;you&#8217;ll need to create it and upload&#8221;  
echo &#8220;your ssh key at git.opendaylight.org&#8221;  
echo &#8220;\***\***\***\***\***\***\***\***&#8221;  
echo &#8220;\***\***\***\***\***\***\***\***&#8221;

echo &#8220;\***\***\***\***\***\***\***\***&#8221;  
echo &#8220;Installing Development tools and other deps&#8221;  
echo &#8220;\***\***\***\***\***\***\***\***&#8221;  
yum install -y wget vim java ant python eclipse-platform git  
yum groupinstall -y “Development tools”A

echo &#8220;\***\***\***\***\***\***\***\***&#8221;  
echo &#8220;Downloading and installing maven&#8221;  
echo &#8220;\***\***\***\***\***\***\***\***&#8221;  
wget http://www.poolsaboveground.com/apache/maven/maven-3/3.0.5/binaries/apache-maven-3.0.5-bin.zip  
unzip apache-maven-3.0.5-bin.zip -d /usr/share/  
ln -s /usr/share/apache-maven-3.0.5/bin/mvn /usr/bin/mvn

echo &#8220;\***\***\***\***\***\***\***\***&#8221;  
echo &#8220;Downloading GIT code&#8221;  
echo &#8220;\***\***\***\***\***\***\***\***&#8221;  
\# Change the username here to your own, you&#8217;ll need to create it and upload  
\# your ssh key at git.opendaylight.org  
mkdir -p /services/opendaylight/  
cd /services/opendaylight/  
git clone https://buraglio@git.opendaylight.org/gerrit/p/controller.git

echo &#8220;\***\***\***\***\***\***\***\***&#8221;  
echo &#8220;Building OpenDaylight Controller with Maven&#8221;  
echo &#8220;\***\***\***\***\***\***\***\***&#8221;  
cd controller/opendaylight/distribution/opendaylight/  
mvn clean install

echo &#8220;\***\***\***\***\***\***\***\***&#8221;  
echo &#8220;Configure Java Env variables&#8221;  
echo &#8220;\***\***\***\***\***\***\***\***&#8221;  
export JAVA\_HOME=/usr/lib/jvm/java-1.6.0-openjdk.x86\_64  
echo &#8220;JAVA\_HOME=/usr/lib/jvm/java-1.6.0-openjdk.x86\_64&#8221; >> /etc/environment

echo &#8220;\***\***\***\***\***\***\***\***&#8221;  
echo &#8220;Load the controller&#8221;  
echo &#8220;\***\***\***\***\***\***\***\***&#8221;  
cd /services/opendaylight/controller/distribution/opendaylight/target/distribution.opendaylight-0.1.0-SNAPSHOT-osgipackage/opendaylight

echo &#8220;\***\***\***\***\***\***\***\***&#8221;  
echo &#8220;Start OpenDaylight OF controller&#8221;  
echo &#8220;\***\***\***\***\***\***\***\***&#8221;  
./run.sh