FROM php:7.2-apache

RUN apt-get upadate && \
    apt-get install -y --no-install-recommends git zip \
    curl --silent --show-error https://getcomposer.org/installer | php \
    pecl install xdebug-2.6.0 \
    && docker-php-ext-enable xdebug \
    && docker-php-ext-install pdo pdo_mysql

WORKDIR /app

COPY php.init /usr/local/etc/php/php.init
COPY . /app/

RUN composer install \
    --ignore-platform-reqs \
    --no-ansi \
    --no-dev \
    --no-interaction \
    --no-scripts