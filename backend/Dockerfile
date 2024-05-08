FROM php:8.2-fpm

# Install required system packages
RUN apt-get update && apt-get install -y \
    git \
    unzip \
    libicu-dev \
    libzip-dev \
    libpq-dev \
    autoconf \
    gcc \
    make \
    && docker-php-ext-install pdo pdo_mysql pdo_pgsql intl zip opcache exif

# Install Node.js and npm
RUN curl -sL https://deb.nodesource.com/setup_lts.x | bash - \
    && apt-get install -y nodejs  

# Install Composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer
WORKDIR /var/www/api.trading.net

CMD ["php-fpm"]

EXPOSE 9000
