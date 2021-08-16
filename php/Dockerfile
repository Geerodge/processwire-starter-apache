FROM php:7.4-apache
WORKDIR /var/www/html/

RUN apt-get update && apt-get install -y \
    imagemagick libmagickwand-dev --no-install-recommends \
    libzip-dev \
    zip \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libpng-dev \
    && pecl install imagick \
    && docker-php-ext-enable imagick \
    && docker-php-ext-install zip \
    && docker-php-ext-install pdo_mysql \
    && docker-php-ext-install mysqli \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) gd


RUN a2enmod rewrite

EXPOSE 80
EXPOSE 443

# Remove all default site files in /var/www/html
RUN rm -rf /var/www/html/*

# Copy app folder files
COPY --chown=www-data:www-data app/ /var/www/html

VOLUME /var/www/html
