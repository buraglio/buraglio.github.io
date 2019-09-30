---
id: 632
title: Scripting the build of OpenDayight Controller under CentOS
date: 2013-05-03T12:36:57-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2013/05/627-revision-5/
permalink: /2013/05/627-revision-5/
---
<a href="https://twitter.com/blinken_lichten" target="_blank">Jon Langemak</a> has a great write up on <a href="http://www.dasblinkenlichten.com/installing-opendaylight-on-centos/" target="_blank">building the OpenDaylight controller under CentOS</a>. Since I&#8217;ll have to do this a bunch of times, I though tI&#8217;d take what he so generously put online and build a very rudimentary script for deploying ODC under CentOS. The prerequisites are that you already have an account and ssh key at the <a href="https://git.opendaylight.org/" target="_blank">OpenDaylight GIT repo</a> and that you <a href="http://www.revsys.com/writings/quicktips/turn-off-selinux.html" target="_blank">disable SELinux</a>.

Here is the script:  
<br />
#!/bin/bash</p>
<p># Install Opendaylight controller under CentOS<br />
# by nick [at] buraglio.com http://www.twitter.com/buraglio<br />
# http://www.forwardingplane.net<br />
# Based on post by Jon Langemak (http://www.twitter.com/blinken_lichten<br />
# http://www.dasblinkenlichten.com/installing-opendaylight-on-centos/</p>
<p>yum="/usr/bin/yum"<br />
servivce="/sbin/service"<br />
chkconfig="/sbin/chkconfig"</p>
<p>echo "************************"<br />
echo "************************"<br />
echo "Disable SELINUX before starting this process"<br />
echo "Edit the /etc/selinux/config file and restart the server"<br />
echo "************************"<br />
echo "************************"<br />
echo "Change the username in the GIT section to your own"<br />
echo "you'll need to create it and upload"<br />
echo "your ssh key at git.opendaylight.org"<br />
echo "************************"<br />
echo "************************"</p>
<p>echo "************************"<br />
echo "Installing Development tools and other deps"<br />
echo "************************"<br />
yum install -y wget vim java ant python eclipse-platform git<br />
yum groupinstall -y “Development tools”A</p>
<p>echo "************************"<br />
echo "Downloading and installing maven"<br />
echo "************************"<br />
wget http://www.poolsaboveground.com/apache/maven/maven-3/3.0.5/binaries/apache-maven-3.0.5-bin.zip<br />
unzip apache-maven-3.0.5-bin.zip -d /usr/share/<br />
ln -s /usr/share/apache-maven-3.0.5/bin/mvn /usr/bin/mvn</p>
<p>echo "************************"<br />
echo "Downloading GIT code"<br />
echo "************************"<br />
# Change the username here to your own, you'll need to create it and upload<br />
# your ssh key at git.opendaylight.org<br />
mkdir -p /services/opendaylight/<br />
cd /services/opendaylight/<br />
git clone https://buraglio@git.opendaylight.org/gerrit/p/controller.git</p>
<p>echo "************************"<br />
echo "Building OpenDaylight Controller with Maven"<br />
echo "************************"<br />
cd controller/opendaylight/distribution/opendaylight/<br />
mvn clean install</p>
<p>echo "************************"<br />
echo "Configure Java Env variables"<br />
echo "************************"<br />
export JAVA_HOME=/usr/lib/jvm/java-1.6.0-openjdk.x86_64<br />
echo "JAVA_HOME=/usr/lib/jvm/java-1.6.0-openjdk.x86_64" >> /etc/environment</p>
<p>echo "************************"<br />
echo "Load the controller"<br />
echo "************************"<br />
cd /services/opendaylight/controller/distribution/opendaylight/target/distribution.opendaylight-0.1.0-SNAPSHOT-osgipackage/opendaylight</p>
<p>echo "************************"<br />
echo "Start OpenDaylight OF controller"<br />
echo "************************"<br />
./run.sh</p>
<p><code></p>