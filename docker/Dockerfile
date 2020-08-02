FROM ubuntu:latest

#updating the system
RUN apt-get update && apt-get install wget -y ; \
apt-get install sudo -y;

#creating a user with sudo privileges and a user for nginx
RUN groupadd --gid 2000 admin && useradd --uid 2000 --gid admin \
--shell /bin/bash --create-home admin && passwd -d admin && \
usermod -aG sudo admin; \
groupadd --gid 2001 nginx-user && useradd --uid 2001 --gid nginx-user \
--shell /bin/bash --create-home nginx-user && passwd -d nginx-user; \
echo "nginx-user ALL=(ALL) NOPASSWD: /usr/sbin/service nginx start,\
/usr/sbin/service nginx stop,/usr/sbin/service nginx restart"\
>>/etc/sudoers


#switching to admin user
USER admin

#installing java, nginx, nettools
RUN sudo apt-get install openjdk-11-jdk -y ; \
sudo apt-get install nginx -y ; \
sudo apt-get install net-tools -y ;

#Copying nginx conf
COPY ./nginx.conf /etc/nginx/nginx.conf 

#switching to nginx-user
USER nginx-user

ENTRYPOINT ["tail", "-f", "/dev/null"]
