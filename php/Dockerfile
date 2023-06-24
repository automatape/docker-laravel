# Utiliza una imagen base de PHP
FROM php:7.4-fpm

# Instala las dependencias requeridas por Laravel
RUN apt-get update && apt-get install -y \
    libonig-dev \
    libxml2-dev \
    zip \
    unzip \
    && docker-php-ext-install pdo_mysql mbstring exif pcntl bcmath opcache

# Instala Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Establece el directorio de trabajo dentro del contenedor
WORKDIR /var/www/html

# Copia los archivos del proyecto Laravel al contenedor
COPY ./laravel-project .

# Instala las dependencias del proyecto Laravel
RUN composer install --optimize-autoloader --no-dev

# Genera la clave de aplicación de Laravel
RUN php artisan key:generate