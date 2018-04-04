FROM raccourci/php:7-cli-alpine

# Install COMPOSER
RUN curl -O https://getcomposer.org/composer.phar && \
    chmod +x composer.phar && \
    mv composer.phar /usr/bin/composer

ENTRYPOINT ["composer"]
