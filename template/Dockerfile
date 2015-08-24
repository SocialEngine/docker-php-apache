FROM php:{{ version }}-apache
MAINTAINER Stepan Mazurov <stepan@socialengine.com>

COPY bin/* /usr/local/bin/

RUN DEBIAN_FRONTEND=noninteractive apt-get update && apt-get install -y \
        libmcrypt-dev \
        zlib1g-dev \
        git \
        && rm -rf /var/lib/apt/lists/*

# You can use this to enable xdebug. start-apache2 script will enable xdebug 
# if PHP_XDEBUG is set to 1
ENV PHP_XDEBUG 0
ENV PHP_TIMEZONE "UTC"

# Setup bare-minimum extra extensions for Laravel & others
RUN docker-php-ext-install mbstring mcrypt zip
RUN docker-php-pecl-install xdebug

# Install composer
RUN curl -sS https://getcomposer.org/installer | php -- \
      --install-dir=/usr/local/bin \
      --filename=composer

# Setup apache
RUN a2enmod rewrite

COPY apache2.conf /etc/apache2/apache2.conf

# Setup App
RUN mkdir -p /app/public && chown -R www-data:www-data /app

WORKDIR /app

ENTRYPOINT ["setup-container"]

CMD ["apache2-foreground"]
