FROM php:8.1.13-fpm-alpine AS app_php

COPY --from=mlocati/php-extension-installer /usr/bin/install-php-extensions /usr/local/bin/

RUN install-php-extensions gd xdebug

RUN apk add --no-cache \
		acl \
		fcgi \
		file \
		gettext \
		git \
	;

RUN set -eux; \
  install-php-extensions \
   	intl \
   	zip \
   	apcu \
	opcache \
   	bz2 \
   	curl \
    fileinfo \
    mbstring \
    exif \
    mysqli \
    pdo_mysql \
    ;

#Install composer
COPY --from=composer:latest /usr/bin/composer /usr/local/bin/composer

# Install NodeJS
RUN apk add --no-cache nodejs npm
