FROM php:8.0-fpm

RUN apt-get update \
    && apt install -y default-mysql-client \
    && docker-php-ext-install pdo_mysql

ADD ./php.ini /usr/local/etc/php/php.ini

