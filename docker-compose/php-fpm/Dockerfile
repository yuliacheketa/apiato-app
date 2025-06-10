FROM php:8.1-fpm-alpine


RUN apk add --no-cache \
    $PHPIZE_DEPS \
    linux-headers \
    postgresql-dev \
    icu-dev \
    git \
    unzip \
    autoconf \
    pkgconf \
    gettext-dev \    
    zlib-dev

RUN docker-php-ext-configure intl && \
    docker-php-ext-install -j$(getconf _NPROCESSORS_ONLN) \
        pdo \
        opcache \
        pdo_pgsql \
        bcmath \
        intl \
        gettext


RUN pecl install xdebug && docker-php-ext-enable xdebug


RUN curl -sS https://getcomposer.org/installer  | php -- --install-dir=/usr/bin --filename=composer && \
    chmod +x /usr/bin/composer

WORKDIR /var/www/html
