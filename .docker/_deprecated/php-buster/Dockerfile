FROM php:7.3-fpm

MAINTAINER Ernest Shefer <shef-er@ya.ru>

RUN apt-get update && apt-get install -y \
        apt-utils \
        git \
        curl \
        wget \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng-dev \
        zlib1g-dev \
        libicu-dev \
        libonig-dev \
        g++ \
        libmagickwand-dev --no-install-recommends \
        libxml2-dev \
    && docker-php-ext-configure gd \
    && docker-php-ext-install -j$(nproc) gd \
    && docker-php-ext-configure intl \
    && docker-php-ext-install intl \
    && docker-php-ext-install mbstring zip xml pdo_mysql iconv \
    && pecl install imagick \
    && docker-php-ext-enable imagick \
    && pecl install mcrypt-1.0.3 \
    && docker-php-ext-enable mcrypt \
    && pecl install xdebug-2.9.0 \
    && docker-php-ext-enable xdebug

RUN wget https://getcomposer.org/installer -O - -q \
    | php -- --install-dir=/bin --filename=composer --quiet

WORKDIR /var/www

EXPOSE 9000

CMD ["php-fpm"]
