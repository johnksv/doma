FROM php:7.4.2-apache

RUN docker-php-ext-install mysqli && docker-php-ext-enable mysqli

# https://medium.com/better-programming/php-how-to-run-your-entire-development-environment-in-docker-containers-on-macos-787784e94f9a
RUN pecl channel-update pecl.php.net; \
    pecl install xdebug-2.9.2; \
    docker-php-ext-enable xdebug

# Delete the resulting ini files created by the PECL install command
RUN rm -rf /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini


RUN mv "$PHP_INI_DIR/php.ini-development" "$PHP_INI_DIR/php.ini"
COPY xdebug-config.ini $PHP_INI_DIR/conf.d/

EXPOSE 9000


COPY dev-config.php /var/www/html/config.php
COPY phpinfo.php /var/www/html/
