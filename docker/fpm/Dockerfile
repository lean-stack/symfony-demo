FROM alpine:3.5

MAINTAINER Micha Alt <mail@lean-stack.de>

# Changelog

# Set timezone
RUN rm /etc/localtime
RUN ln -s /usr/share/zoneinfo/Europe/Berlin /etc/localtime

RUN apk add --update \
    openssl \
    bash \
    curl \
    git \
    php7 \
    php7-fpm \
    php7-apcu \
    php7-ctype \
    php7-dom \
    php7-iconv \
    php7-intl \
    php7-opcache \
    php7-json \
    php7-mcrypt \
    php7-mysqli \
    php7-pdo \
    php7-pdo_mysql \
    php7-phar \
    php7-posix \
    php7-openssl \
    php7-session \
    php7-xdebug \
    php7-xml \
    php7-zlib

RUN rm -rf /var/cache/apk/* && rm -rf /tmp/*

RUN ln -s /usr/bin/php7 /usr/bin/php \
 && ln -s /usr/sbin/php-fpm7  /usr/sbin/php-fpm \
 && ln -s /etc/php7 /etc/php \
 && ln -s /usr/lib/php7 /usr/lib/php

COPY rootfs/ /

RUN chmod a+x /usr/local/bin/composer-install.sh && composer-install.sh

CMD ["php-fpm", "-F"]

WORKDIR /project
