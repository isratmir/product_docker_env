FROM php:7.2-fpm

#COPY imagick.so /usr/local/lib/php/extensions/no-debug-non-zts-20170718/

RUN docker-php-ext-install mysqli
#RUN docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr
#RUN docker-php-ext-install gd
# RUN apt-get -yqq update
# RUN apt-get -yqq install exiftool
# RUN docker-php-ext-configure exif
RUN docker-php-ext-install exif
# RUN docker-php-ext-enable exif

RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng-dev \
    && docker-php-ext-install -j$(nproc) iconv \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd

RUN export CFLAGS="$PHP_CFLAGS" CPPFLAGS="$PHP_CPPFLAGS" LDFLAGS="$PHP_LDFLAGS" \
    #&& apt-get update \
    && apt-get install -y --no-install-recommends \
        libmagickwand-dev \
    && rm -rf /var/lib/apt/lists/* \
    && pecl install imagick-3.4.3 \
    && docker-php-ext-enable imagick