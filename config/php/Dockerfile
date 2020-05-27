ARG PHP_VERSION
FROM php:${PHP_VERSION}-fpm-alpine

LABEL maintainer="Stefan Koolen <stefan@fonkel.io>"

RUN apk --update --no-cache add   zlib-dev \
                                  libpng-dev \
                                  libzip-dev \
                                  oniguruma-dev \
                                  curl

RUN docker-php-ext-install  gd \
                            zip \ 
                            pdo_mysql \
                            mbstring \
                            opcache


EXPOSE 9000

RUN php