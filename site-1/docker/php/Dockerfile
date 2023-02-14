FROM php:7.4-fpm
RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng-dev \ 
				libzip-dev \ 
				libxml2-dev \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) gd \
		mysqli \
		opcache \
		zip \
		pdo \
		pdo_mysql;


COPY php.ini /usr/local/etc/php/conf.d/
