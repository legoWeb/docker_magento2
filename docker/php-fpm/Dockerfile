#http://developerblog.redhat.com/2014/12/29/running-php-fpm-in-docker/
#start with a redhat install
FROM centos:7

MAINTAINER Tom Scott-Malden tom@skywire.co.uk

LABEL com.skywire.container="Php-Fpm"
LABEL version="0.0.1"
LABEL description="Skywire php-fpm7.0 Docker container"
RUN yum -y update && yum clean all
#RUN rpm -Uvh https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
#RUN rpm -Uvh https://mirror.webtatic.com/yum/el7/webtatic-release.rpm
RUN yum install -y http://dl.iuscommunity.org/pub/ius/stable/CentOS/7/x86_64/ius-release-1.0-14.ius.centos7.noarch.rpm
RUN yum -y update
RUN yum -y install php71u-fpm php71u-intl  php71u-pdo php71u-mysqlnd php71u-devel php71u-mbstring php71u-soap php71u-xml php71u-json php71u-iconv  php71u-opcache php71u-mysql php71u-gd php71u-mcrypt php71u-bcmath php71u-pecl-xdebug && yum clean all
RUN useradd -s /bin/false nginx
RUN usermod -u 1000 nginx
COPY src/skywire_updates.ini /etc/php.d/skywire_updates.ini
RUN sed -e 's/127.0.0.1:9000/9000/' \
        -e 's/apache/nginx/' \
        -e '/allowed_clients/d' \
        -e '/catch_workers_output/s/^;//' \
        -e '/error_log/d' \
        -i /etc/php-fpm.d/www.conf
RUN mkdir -p /var/www/html
VOLUME /var/www/html
EXPOSE 9000
ENTRYPOINT /usr/sbin/php-fpm --nodaemonize
