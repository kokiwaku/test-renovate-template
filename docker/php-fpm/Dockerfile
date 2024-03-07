FROM php:8.3-fpm-bullseye@sha256:0e8be91ab1a9ac0e151e04c85aef23aa0885b36ff906df172db60122ef60ba61

COPY --from=composer:2.7@sha256:da5213f1c0c4db435ad335be4e782ebf8677b45d37677a6db1e73e474c7ad947 /usr/bin/composer /usr/bin/composer

RUN apt-get update && apt-get install -y libpq-dev \
    git \
    libzip-dev \
    zip \
    && docker-php-ext-install zip pdo pgsql pdo_pgsql \
    && pecl install xdebug \
    && docker-php-ext-enable xdebug

COPY ./ini /usr/local/etc/php/conf.d/

WORKDIR /workspace