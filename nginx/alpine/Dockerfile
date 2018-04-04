FROM nginx:alpine

ENV LOCALTIME Europe/Paris

RUN apk add --no-cache --update --virtual .tzdata-deps tzdata && \
    cp /usr/share/zoneinfo/$LOCALTIME /etc/localtime && \
    echo $LOCALTIME > /etc/timezone

RUN rm -rf /tmp/* && \
    apk del .tzdata-deps
