FROM php:7.2-fpm

RUN docker-php-ext-install mysqli

COPY ./php/imagick.so /usr/local/lib/php/extensions/no-debug-non-zts-20170718/

# RUN apt-get update && apt-get install -y \
#     libmagickwand-dev --no-install-recommends \
#     && pecl install imagick \
# 	&& docker-php-ext-enable imagick