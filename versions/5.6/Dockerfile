FROM php:5.6-apache
MAINTAINER Stepan Mazurov <stepan@socialengine.com>

COPY bin/* /usr/local/bin/

RUN DEBIAN_FRONTEND=noninteractive apt-get update && apt-get install -y \
        libmcrypt-dev \
        zlib1g-dev \
        git \
        && rm -rf /var/lib/apt/lists/*

# Setup bare-minimum extra extensions for Laravel & others
ENV PHP_XDEBUG 0

RUN docker-php-ext-install mbstring mcrypt zip
RUN docker-php-pecl-install xdebug

# Install composer
RUN curl -sS https://getcomposer.org/installer | php -- \
      --install-dir=/usr/local/bin \
      --filename=composer \

# Setup apache
RUN a2enmod rewrite

COPY apache2.conf /etc/apache2/apache2.conf

# Setup App
RUN mkdir -p /app/public && chown -R www-data:www-data /app

WORKDIR /app

CMD ["start-apache2"]
