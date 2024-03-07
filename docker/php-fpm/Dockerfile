FROM php:8.2-fpm-bullseye@sha256:90ce145889273a6689d32a907bb5ebd1d5eed0721c2e3f8023f8b3cad05d58fe

COPY --from=composer:2.6@sha256:eacc7de1c1f6554a2acc49ca9ca3fff57ca4567e626e778c43d0ac0bc2d54b43 /usr/bin/composer /usr/bin/composer

RUN apt-get update && apt-get install -y libpq-dev \
    git \
    libzip-dev \
    zip \
    && docker-php-ext-install zip pdo pgsql pdo_pgsql \
    && pecl install xdebug \
    && docker-php-ext-enable xdebug

COPY ./ini /usr/local/etc/php/conf.d/

WORKDIR /workspace