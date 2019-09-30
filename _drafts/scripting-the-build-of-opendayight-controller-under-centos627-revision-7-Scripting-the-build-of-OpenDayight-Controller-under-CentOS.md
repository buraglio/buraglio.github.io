---
id: 634
title: Scripting the build of OpenDayight Controller under CentOS
date: 2013-05-03T12:37:40-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2013/05/627-revision-7/
permalink: /2013/05/627-revision-7/
---
<a href="https://twitter.com/blinken_lichten" target="_blank">Jon Langemak</a> has a great write up on <a href="http://www.dasblinkenlichten.com/installing-opendaylight-on-centos/" target="_blank">building the OpenDaylight controller under CentOS</a>. Since I&#8217;ll have to do this a bunch of times, I though tI&#8217;d take what he so generously put online and build a very rudimentary script for deploying ODC under CentOS. The prerequisites are that you already have an account and ssh key at the <a href="https://git.opendaylight.org/" target="_blank">OpenDaylight GIT repo</a> and that you <a href="http://www.revsys.com/writings/quicktips/turn-off-selinux.html" target="_blank">disable SELinux</a>.

Here is the script:

<pre>#!/bin/bash

# Install Opendaylight controller under CentOS
# by nick [at] buraglio.com http://www.twitter.com/buraglio
# http://www.forwardingplane.net
# Based on post by Jon Langemak (http://www.twitter.com/blinken_lichten
# http://www.dasblinkenlichten.com/installing-opendaylight-on-centos/

yum="/usr/bin/yum"
servivce="/sbin/service"
chkconfig="/sbin/chkconfig"

echo "************************"
echo "************************"
echo "Disable SELINUX before starting this process"
echo "Edit the /etc/selinux/config file and restart the server"
echo "************************"
echo "************************"
echo "Change the username in the GIT section to your own"
echo "you'll need to create it and upload"
echo "your ssh key at git.opendaylight.org"
echo "************************"
echo "************************"

echo "************************"
echo "Installing Development tools and other deps"
echo "************************"
yum install -y wget vim java ant python eclipse-platform git
yum groupinstall -y “Development tools”A

echo "************************"
echo "Downloading and installing maven"
echo "************************"
wget http://www.poolsaboveground.com/apache/maven/maven-3/3.0.5/binaries/apache-maven-3.0.5-bin.zip
unzip apache-maven-3.0.5-bin.zip -d /usr/share/
ln -s /usr/share/apache-maven-3.0.5/bin/mvn /usr/bin/mvn

echo "************************"
echo "Downloading GIT code"
echo "************************"
# Change the username here to your own, you'll need to create it and upload
# your ssh key at git.opendaylight.org
mkdir -p /services/opendaylight/
cd /services/opendaylight/
git clone https://buraglio@git.opendaylight.org/gerrit/p/controller.git

echo "************************"
echo "Building OpenDaylight Controller with Maven"
echo "************************"
cd controller/opendaylight/distribution/opendaylight/
mvn clean install

echo "************************"
echo "Configure Java Env variables"
echo "************************"
export JAVA_HOME=/usr/lib/jvm/java-1.6.0-openjdk.x86_64
echo "JAVA_HOME=/usr/lib/jvm/java-1.6.0-openjdk.x86_64" &gt;&gt; /etc/environment

echo "************************"
echo "Load the controller"
echo "************************"
cd /services/opendaylight/controller/distribution/opendaylight/target/distribution.opendaylight-0.1.0-SNAPSHOT-osgipackage/opendaylight

echo "************************"
echo "Start OpenDaylight OF controller"
echo "************************"
./run.sh
</pre>