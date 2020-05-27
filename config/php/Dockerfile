FROM php:7.4-fpm-alpine

RUN apk --update add  zlib-dev \
                      libpng-dev \
                      libzip-dev \
                      curl

RUN docker-php-ext-install gd zip pdo_mysql

EXPOSE 9000

RUN php