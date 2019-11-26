FROM php:7.2-fpm-stretch

# Install any custom system requirements
RUN set -ex; \
	sed -i '/jessie-updates/d' /etc/apt/sources.list && \
	apt-get update && \
	apt-get install -y \
		curl \
		libfreetype6-dev \
		libmcrypt-dev \
		libpng-dev \
		libwebp-dev \
		libjpeg62-turbo-dev \
		libjpeg-dev \
		libpng-dev \
		libgmp-dev \
		libldap2-dev \
		vim \
		libmcrypt-dev \
		zlib1g-dev \
		libzip-dev\
		libxml2-dev \
		&& pecl install redis \
		&& pecl install mcrypt-1.0.2 \
	&& apt-get clean -y \
	&& rm -rf /var/lib/apt/lists/* ; \

# Install various PHP
docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ && \
docker-php-ext-configure zip && \
docker-php-ext-configure calendar && \
docker-php-ext-configure pdo_mysql --with-pdo-mysql; \
	docker-php-ext-install \
		calendar \
		mysqli \
		opcache \
		zip \
		pdo \
		gd \
		bcmath \
		pdo_mysql; 

#RUN echo "max_file_uploads=10G" >> /usr/local/etc/php/conf.d/docker-php-ext-max_file_uploads.ini
#RUN echo "post_max_size=10G" >> /usr/local/etc/php/conf.d/docker-php-ext-post_max_size.ini
#RUN echo "upload_max_filesize=10G" >> /usr/local/etc/php/conf.d/docker-php-ext-upload_max_filesize.ini

COPY php.ini /usr/local/etc/php/conf.d/
