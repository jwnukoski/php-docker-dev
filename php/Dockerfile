FROM php:8.2.14-fpm

RUN apt update
RUN apt install git -y
RUN pecl install xdebug \
    && docker-php-ext-enable xdebug

COPY ./conf.d/xdebug.ini /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
COPY ./conf.d/error_reporting.ini /usr/local/etc/php/conf.d/error_reporting.ini
COPY ./php.ini /usr/local/etc/php/php.ini

# Install Symfony CLI
RUN curl -sS https://get.symfony.com/cli/installer | bash
# Add Symfony CLI to PATH
RUN ln -s /root/.symfony5/bin/symfony /usr/local/bin/symfony

# Composer
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" && \
php -r "if (hash_file('sha384', 'composer-setup.php') === 'dac665fdc30fdd8ec78b38b9800061b4150413ff2e3b6f88543c636f7cd84f6db9189d43a81e5503cda447da73c7e5b6') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;" && \
php composer-setup.php && \
php -r "unlink('composer-setup.php');" && \
mv composer.phar /usr/local/bin/composer

WORKDIR /var/www/html/workspace