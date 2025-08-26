# Backend Dockerfile - Laravel
FROM php:8.2-fpm

# Inštalácia systémových závislostí
RUN apt-get update && apt-get install -y \
    mariadb-client \
    libpng-dev \
    libjpeg-dev \
    libonig-dev \
    libxml2-dev \
    zip \
    unzip \
    git \
    curl \
    && docker-php-ext-install pdo_mysql mbstring exif pcntl bcmath gd

# Composer
COPY --from=composer:2 /usr/bin/composer /usr/bin/composer

WORKDIR /var/www/html

# Kopírovanie kódu
COPY . .

# Inštalácia PHP závislostí Laravel
RUN composer install --no-interaction --prefer-dist

# Nastavenie práv
RUN chown -R www-data:www-data /var/www/html \
    && chmod -R 755 /var/www/html

EXPOSE 80

CMD php artisan serve --host=0.0.0.0 --port=80
