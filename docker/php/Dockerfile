FROM php:7.4-fpm

RUN apt-get update && apt-get install -y \
    curl \
    wget \
    libpq-dev \
    zlib1g-dev \
    libmcrypt-dev \
    libzip-dev \
    && /usr/local/bin/docker-php-ext-install pgsql pdo_pgsql zip

RUN pecl install -o -f redis \
    &&  rm -rf /tmp/pear \
    &&  docker-php-ext-enable redis

RUN wget https://getcomposer.org/installer -O - -q | php -- --install-dir=/bin --filename=composer --quiet

WORKDIR /app

RUN chown -R 1000:1000 /app

USER 1000
