ARG PHP_VERSION=7.2
ARG NGINX_VERSION=1.15

FROM php:${PHP_VERSION}-fpm-alpine AS application_php
WORKDIR /var/www/application
COPY . ./
VOLUME /var/www/application

FROM nginx:${NGINX_VERSION}-alpine AS application_nginx
COPY docker/nginx/conf.d/default.conf /etc/nginx/conf.d/default.conf
WORKDIR /var/www/application
COPY --from=application_php /var/www/application/public public/