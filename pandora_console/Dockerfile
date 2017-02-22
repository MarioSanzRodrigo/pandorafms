FROM centos:centos6
MAINTAINER Pandora FMS Team <info@pandorafms.com>

RUN { \
	echo '[EPEL]'; \
	echo 'name = CentOS Epel'; \
	echo 'baseurl = http://dl.fedoraproject.org/pub/epel/6/x86_64'; \
	echo 'enabled=1'; \
	echo 'gpgcheck=0'; \
} > /etc/yum.repos.d/extra_repos.repo

RUN { \
        echo '[artica_pandorafms]'; \
        echo 'name=CentOS6 - PandoraFMS official repo'; \
        echo 'baseurl=http://artica.es/centos6'; \
        echo 'gpgcheck=0'; \
        echo 'enabled=1'; \
} > /etc/yum.repos.d/pandorafms.repo

RUN yum -y update; yum clean all;
RUN yum install -y \ 
	git \
	httpd \
	cronie \
	ntp \
	openldap \
	anytermd \
	nfdump \
	wget \
	curl \
	openldap \
	plymouth \
	xterm \
	php \ 
	php-gd \ 
	graphviz \ 
	php-mysql \ 
	php-pear-DB \ 
	php-pear \
	php-pdo \
	php-mbstring \ 
	php-ldap \ 
	php-snmp \ 
	php-ldap \ 
	php-common \ 
	php-zip \ 
	nmap \
	net-snmp-utils \
	xprobe2 \
	nano \
	nc


COPY pandorafms /tmp/pandorafms

#Exposing ports for: Tentacle protocol
EXPOSE 41121

# Simple startup script to avoid some issues observed with container restart
ADD docker_entrypoint.sh /entrypoint_console.sh
RUN chmod -v +x /entrypoint_console.sh

CMD ["/entrypoint_console.sh"]

