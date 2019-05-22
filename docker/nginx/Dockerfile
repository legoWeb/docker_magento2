#get oficial docker image
FROM nginx

MAINTAINER Tom Scott-Malden tom@skywire.co.uk

LABEL com.skywire.container="Nginx"
LABEL version="0.0.1"
LABEL description="Skywire Nginx Docker container"

#allow ports through
EXPOSE 80 443

COPY src/template.conf /etc/nginx/conf.d/template.conf

#update nginx user to UID 1000
RUN usermod -u 1000 nginx

#mount the dir
VOLUME /var/www/html

#create SSL certificates
RUN apt-get update; apt-get install openssl
RUN openssl genrsa -out /etc/ssl/site.key 2048
RUN openssl req -x509 -newkey rsa:2048 -keyout /etc/ssl/site.key -out /etc/ssl/site.crt -days 365 -nodes -subj '/CN=docker.webmeridian.local'
