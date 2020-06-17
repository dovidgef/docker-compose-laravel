FROM php:7.4-fpm-buster

RUN apt-get update && apt-get install -y --no-install-recommends libbz2-dev libenchant-dev libpng-dev libldap2-dev libgmp-dev libc-client-dev libkrb5-dev libicu-dev \
    libmcrypt-dev libxml2-dev libmagickwand-dev libzip-dev unzip

RUN docker-php-ext-configure ldap --with-libdir=lib/x86_64-linux-gnu/ && \
    docker-php-ext-configure imap --with-kerberos --with-imap-ssl && \
    docker-php-ext-install ldap mysqli pdo pdo_mysql bcmath bz2 calendar exif zip intl gmp soap gd dom imap sockets

RUN pecl install imagick xdebug-2.9.0 && docker-php-ext-enable imagick xdebug

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

ARG USER_ID
ARG GROUP_ID

# Switch local user to be www-data user
RUN usermod -u ${USER_ID} www-data && groupmod -g ${GROUP_ID} www-data

RUN chown -R www-data:www-data /var/www

USER www-data

WORKDIR /var/www/html

