FROM php:5.6-apache

MAINTAINER Stepan Mazurov <stepan@socialengine.com>

RUN DEBIAN_FRONTEND=noninteractive apt-get update && apt-get install -y \
        libmcrypt-dev \
        zlib1g-dev \
        git \
        && rm -rf /var/lib/apt/lists/*

RUN docker-php-ext-install mbstring mcrypt zip

RUN mkdir -p /app/public && chown -R www-data:www-data /app

WORKDIR /app

RUN curl -sS https://getcomposer.org/installer | php && \
    mv composer.phar /usr/local/bin/composer

COPY apache2.conf /etc/apache2/apache2.conf
