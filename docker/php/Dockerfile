FROM php:7.4-fpm

RUN apt-get update && apt-get install -y \
    curl \
    wget \
    libpq-dev \
    zlib1g-dev \
    libmcrypt-dev \
    libzip-dev \
    sudo \
    && /usr/local/bin/docker-php-ext-install pgsql pdo_pgsql zip

RUN useradd -m docker && echo "docker:docker" | chpasswd && adduser docker sudo

RUN pecl install -o -f redis \
    &&  rm -rf /tmp/pear \
    &&  docker-php-ext-enable redis

RUN wget https://getcomposer.org/installer -O - -q | php -- --install-dir=/bin --filename=composer --quiet

RUN wget https://get.symfony.com/cli/installer -O - | bash

RUN mv ~/.symfony/bin/symfony /usr/local/bin/symfony

WORKDIR /var/html

RUN chown -R 1000:1000 /var/html

USER 1000
