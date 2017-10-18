FROM centos:5.11

RUN set -xe; \
	sed -i -e "s/mirrorlist/#mirrorlist/g" /etc/yum.repos.d/CentOS-Base.repo ; \
        sed -i -e "s/#baseurl/baseurl/g" /etc/yum.repos.d/CentOS-Base.repo ;\ 
        sed -i -e "s/mirror\.centos\.org\/centos/vault.centos.org/g" /etc/yum.repos.d/CentOS-Base.repo ; \
        sed -i -e "s/\$releasever/5.11/g" /etc/yum.repos.d/CentOS-Base.repo ; \
	rm -f /etc/yum.repos.d/libselinux.repo ; \
	yum -y update; \
	yum -y install openssh-server; \
        yum -y install openssh-clients; \
	yum -y install python; \
	sed -i -e "s/#PermitRootLogin.*$/PermitRootLogin yes/" /etc/ssh/sshd_config; \
	sed -i -e "s/^HostKey/#HostKey/g" /etc/ssh/sshd_config; \
	echo "root:admin" | chpasswd ;\
	ssh-keygen -f /etc/ssh/ssh_host_rsa_key -N '' -t rsa ; \
	ssh-keygen -f /etc/ssh/ssh_host_dsa_key -N '' -t dsa ; 
	

ENTRYPOINT /usr/sbin/sshd && bash	
