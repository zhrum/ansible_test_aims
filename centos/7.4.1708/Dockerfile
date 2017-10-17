FROM centos:7.4.1708

RUN set -xe; \
	yum -y update; \
	yum -y install openssh-server; \
        yum -y install openssh-clients; \
	yum -y install python; \
	sed -i -e "s/#PermitRootLogin.*$/PermitRootLogin yes/" /etc/ssh/sshd_config; \
	sed -i -e "s/^HostKey/#HostKey/g" /etc/ssh/sshd_config; \
	echo "root:admin" | chpasswd ;\
	ssh-keygen -f /etc/ssh/ssh_host_rsa_key -N '' -t rsa ; \
	ssh-keygen -f /etc/ssh/ssh_host_dsa_key -N '' -t dsa ; \
	ssh-keygen -f /etc/ssh/ssh_host_ecdsa_key -N '' -t ecdsa ; \
	ssh-keygen -f /etc/ssh/ssh_host_ed25519_key -N '' -t ed25519 ; 
	
ENTRYPOINT /usr/sbin/sshd && bash
