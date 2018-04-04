FROM node:9-alpine

ENV LOCALTIME Europe/Paris
ENV NPM_DEPS make g++ automake autoconf libtool nasm

RUN apk add --no-cache --update \
    nano \
    wget \
    curl \
    git \
    openssh \
    openssl \
    $NPM_DEPS

RUN apk add --no-cache --update --virtual .tzdata-deps tzdata && \
    cp /usr/share/zoneinfo/$LOCALTIME /etc/localtime && \
    echo $LOCALTIME > /etc/timezone && \
    apk del .tzdata-deps
