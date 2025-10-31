FROM php:8.3-apache

# Apache rewrite
RUN a2enmod rewrite
WORKDIR /var/www/html

# PHP拡張 (MySQL)
RUN docker-php-ext-install pdo_mysql

# Node.js (Vite用)
RUN curl -fsSL https://deb.nodesource.com/setup_20.x | bash - \
    && apt-get install -y nodejs

# pnpm追加
RUN npm install -g pnpm

# Composer
COPY --from=composer:2 /usr/bin/composer /usr/bin/composer

COPY 000-default.conf /etc/apache2/sites-available/000-default.conf 