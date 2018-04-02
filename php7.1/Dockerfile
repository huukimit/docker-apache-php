FROM ubuntu:16.04

MAINTAINER Nguyen Huu Kim <kimnguyen.ict@gmail.com>

RUN apt-get update \
    && apt-get install -y software-properties-common locales \
    && locale-gen en_US.UTF-8

ENV LANGUAGE=en_US.UTF-8
ENV LC_ALL=en_US.UTF-8
ENV LC_CTYPE=UTF-8
ENV LANG=en_US.UTF-8
ENV TERM xterm

ENV APACHE_RUN_USER www-data
ENV APACHE_RUN_GROUP www-data
ENV APACHE_LOG_DIR /var/log/apache2

RUN add-apt-repository ppa:ondrej/php \
  && apt-get update \
  && apt-get install -y php7.1 libapache2-mod-php7.1 --force-yes

RUN apt-get install -y \
    php7.1-mysql \
    php7.1-common \
    php7.1-mbstring \
    php7.1-xml \
    php7.1-json \
    php7.1-tokenizer

RUN echo "ServerName localhost" >> /etc/apache2/apache2.conf
RUN apt-get install -y curl nano iputils-ping

EXPOSE 80
EXPOSE 443

WORKDIR /var/www/html

ENTRYPOINT service apache2 restart && /bin/bash
