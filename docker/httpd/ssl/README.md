Minimal Apache HTTPD SSL Configuration
==================================

This is a minimal SSL configuration for apache httpd.  It assumes artifactory and httpd are running on the same machine.
You can use artifactory.conf as a starting point for your installation.

To run the demo:

docker build --rm --tag art_apache_https .
docker run -d --name art_apache_https art_apache_https

#To find the IP of the newly running container use:
docker inspect --format '{{ .NetworkSettings.IPAddress }}' art_apache_https

__Note__
This assumes a file named local.sh that contains something like:

<pre>
sed -i '/mirrorlist/d;s/#baseurl/baseurl/;s~mirror.centos.org~artifactory-us.jfrog.info/artifactory~' /etc/yum.repos.d/CentOS-*.repo
rm /etc/yum.repos.d/Artifactory*
</pre>

This edits the CentOS yum repositories to point at your local artifactory.  Change the artifactory-us.jfrog.info to your
local artifactory instance.

We supply a blank one here so the Dockerfile works.

