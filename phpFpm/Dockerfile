FROM php:8.2-fpm

WORKDIR /srv

RUN apt-get update && apt-get install -y libpq-dev

RUN docker-php-ext-install mysqli pdo pdo_mysql

RUN export DEBIAN_FRONTEND="noninteractive" \
    && apt-get update -qq \
    && apt-get -qqy install software-properties-common apt-utils locales tzdata \
    && apt-get install -y --no-install-recommends procps inotify-tools

RUN apt-get update && apt-get install -y git nano libmcrypt-dev

# zip
RUN apt-get install -y \
        libzip-dev \
        zip \
        unzip \
  && docker-php-ext-install zip

# intl
RUN apt-get install -y zlib1g-dev libicu-dev g++ \
&& docker-php-ext-configure intl \
&& docker-php-ext-install intl

# gd
RUN apt-get update && apt-get install -y libpng-dev
RUN apt-get install -y \
    libwebp-dev \
    libjpeg62-turbo-dev \
    libpng-dev libxpm-dev \
    libfreetype6-dev
RUN docker-php-ext-install gd

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
