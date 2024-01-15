FROM php:8.2.14-fpm

RUN pecl install xdebug \
    && docker-php-ext-enable xdebug

COPY ./conf.d/xdebug.ini /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
COPY ./conf.d/error_reporting.ini /usr/local/etc/php/conf.d/error_reporting.ini
COPY ./php.ini /usr/local/etc/php/php.ini

EXPOSE 9003