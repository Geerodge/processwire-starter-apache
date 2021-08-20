FROM php:7.4-apache

# Install php dependencies
RUN apt-get update && apt-get install -y curl \
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

# Install nodejs and yarn
RUN curl --silent --location https://deb.nodesource.com/setup_12.x | bash -
RUN apt-get install -y \
    nodejs
RUN npm install -g yarn
RUN echo "Node: " && node -v
RUN echo "Yarn: " && yarn --version

RUN a2enmod rewrite

EXPOSE 80
EXPOSE 443

WORKDIR /var/www/html/site/

# Copy app folder files
COPY --chown=www-data:www-data /app /var/www/html

# Install npm/yarn packages
RUN yarn && yarn build

## Run yarn && yarn build && yarn watch locally in app/site
