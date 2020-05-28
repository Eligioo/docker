FROM nginx:1.17.10-alpine

LABEL maintainer="Stefan Koolen <stefan@fonkel.io>"

RUN apk --update --no-cache add   openssl \
                                  bash

RUN set -x ; \
    addgroup -g 82 -S www-data ; \
    adduser -u 82 -D -S -G www-data www-data && exit 0 ; exit 1

COPY ./files/nginx.conf /etc/nginx/
COPY ./files/default.conf /etc/nginx/conf.d/default.conf

ADD ./files/startup.sh /opt/startup.sh
CMD ["/bin/bash", "/opt/startup.sh"]