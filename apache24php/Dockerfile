FROM ubuntu:trusty

MAINTAINER "The Galactic Empire"

ENV DEBIAN_FRONTEND noninteractive

RUN locale-gen en_GB.UTF-8
RUN update-locale LANG=en_GB.UTF-8
RUN update-locale LANGUAGE=en_GB.UTF-8
RUN update-locale LC_ALL=en_GB.UTF-8
RUN apt-get -qq update
RUN apt-get install -y apache2 \
                       libapache2-mod-php5 \
                       libapache2-mod-log-sql-ssl \
                       php5-odbc \
                       php5-curl \
                       php5-gd \
                       php5-mysql \
                       php5-imap \
                       php5-memcache \
                       php5-memcached \
                       php5-sybase \
                       php5-sqlite

VOLUME ["/var/www"]

EXPOSE 80 443

ENV APACHE_RUN_USER www-data
ENV APACHE_RUN_GROUP www-data
ENV APACHE_LOG_DIR /var/log/apache2
ENV APACHE_LOCK_DIR /var/lock/apache2
ENV APACHE_PID_FILE /var/run/apache2.pid

# Default command to run
CMD ["/usr/sbin/apache2", "-D", "FOREGROUND"]
