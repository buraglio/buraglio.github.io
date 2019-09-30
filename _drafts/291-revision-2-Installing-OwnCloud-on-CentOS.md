---
id: 334
title: Installing OwnCloud on CentOS
date: 2013-01-05T16:20:23-06:00
author: Nick Buraglio
layout: revision
guid: http://www.forwardingplane.net/2013/01/291-revision-2/
permalink: /2013/01/291-revision-2/
---
<pre>wget http://dl.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm
wget http://rpms.famillecollet.com/enterprise/remi-release-6.rpm
yum -y install apache2 php5 php5-json php-xml php-mbstring php5-zip php5-gd
yum -y install php5-sqlite curl libcurl3 libcurl3-dev php5-curl php-pd</pre>

php5-sqlite isn&#8217;t available in the repos I use. I wasn&#8217;t able to find it elsewhere either. Per <a href="http://php.net/manual/de/sqlite.installation.php " target="_blank">this page</a>, I have to install it by source.

<pre>cd /etc/yum.repos.d/
wget http://download.opensuse.org/repositories/isv:ownCloud:community/CentOS_CentOS-6/isv:ownCloud:community.repo
yum install owncloud</pre>