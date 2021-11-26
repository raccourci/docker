FROM php:7-cli-alpine3.7

ENV LOCALTIME=Europe/Paris

RUN apk add --no-cache --update \
    nano \
    wget \
    curl \
    git \
    openssh \
    openssl \
    libmemcached-libs \
    mysql-client \
    yaml \
    zlib \
    freetype \
    libpng \
    libjpeg-turbo \
    libjpeg-turbo-utils

RUN apk add --no-cache --update --virtual .phpize-deps $PHPIZE_DEPS && \
    apk add --no-cache --update --virtual .tzdata-deps tzdata && \
    cp /usr/share/zoneinfo/$LOCALTIME /etc/localtime && \
    echo $LOCALTIME > /etc/timezone

RUN apk add --no-cache --update zlib libmemcached-libs && \
    apk add --no-cache --update --virtual .memcached-deps zlib-dev libmemcached-dev cyrus-sasl-dev && \
    pecl install memcached && \
    docker-php-ext-enable memcached

RUN apk add --no-cache --update yaml && \
    apk add --no-cache --update --virtual .yaml-deps yaml-dev && \
    pecl install yaml && \
    docker-php-ext-enable yaml

RUN apk add --no-cache --update freetype libpng libjpeg-turbo libjpeg-turbo-utils imagemagick && \
    apk add --no-cache --update --virtual .gd-deps freetype-dev libpng-dev libjpeg-turbo-dev && \
    docker-php-ext-configure gd \
    --with-gd \
    --with-freetype-dir=/usr/include/ \
    --with-png-dir=/usr/include/ \
    --with-jpeg-dir=/usr/include/ && \
    NPROC=$(grep -c ^processor /proc/cpuinfo 2>/dev/null || 1) && \
    docker-php-ext-install -j${NPROC} gd

RUN apk add --no-cache --update icu zlib && \
    apk add --no-cache --update --virtual .intl-deps icu-dev zlib-dev g++ && \
    docker-php-ext-install intl

RUN apk add --no-cache --update freetype mysql-client && \
    docker-php-ext-configure pdo_mysql --with-pdo-mysql=mysqlnd && \
    docker-php-ext-configure mysqli --with-mysqli=mysqlnd && \
    docker-php-ext-install pdo_mysql && \
    docker-php-ext-install mysqli

RUN docker-php-ext-install opcache && \
    docker-php-ext-install zip

RUN echo "memory_limit=-1" > "$PHP_INI_DIR/conf.d/memory-limit.ini" && \
    echo "date.timezone=${PHP_TIMEZONE:-UTC}" > "$PHP_INI_DIR/conf.d/date_timezone.ini"

RUN rm -rf /usr/share/php7 && \
    rm -rf /tmp/* && \
    apk del .tzdata-deps .phpize-deps .memcached-deps .intl-deps .yaml-deps .gd-deps
