FROM debian:8.9

RUN set -xe;\
   apt-get update; \ 
   apt-get -y install ssh;\
   apt-get -y install python;\
   echo "root:admin" | chpasswd ;\
   sed -i -e "s/PermitRootLogin.*$/PermitRootLogin yes/" /etc/ssh/sshd_config; \
   sed -i -e "s/#PasswordAuthentication.*$/PasswordAuthentication yes/" /etc/ssh/sshd_config;
   
ENTRYPOINT service ssh start && bash
