FROM raccourci/php:7-cli

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

# Config PHP
RUN echo "memory_limit=-1" > "$PHP_INI_DIR/conf.d/memory-limit.ini" && \
    echo "date.timezone=${PHP_TIMEZONE:-UTC}" > "$PHP_INI_DIR/conf.d/date_timezone.ini"

# Install COMPOSER
RUN curl -O https://getcomposer.org/composer.phar && \
    chmod +x composer.phar && \
    mv composer.phar /usr/bin/composer

ENTRYPOINT ["composer"]
