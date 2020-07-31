FROM ubuntu:latest
RUN apt-get update && apt-get install wget -y ; \
apt-get install openjdk-11-jdk -y ; \
apt-get install nginx -y ; \
apt-get install net-tools -y ;\

CMD ["nginx", "-g", "daemon off;"]
