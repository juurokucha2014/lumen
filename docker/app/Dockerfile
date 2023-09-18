FROM php:8.3-rc-fpm

RUN apt-get update && apt-get install -y zlib1g-dev libzip-dev && docker-php-ext-install zip pdo_mysql
RUN apt-get clean

#Composer install
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
&& php composer-setup.php \
&& php -r "unlink('composer-setup.php');" \
&& mv composer.phar /usr/local/bin/composer

ENV COMPOSER_ALLOW_SUPERUSER 1
ENV COMPOSER_HOME /composer
ENV PATH $PATH:/composer/vendor/bin

COPY php.ini /usr/local/etc/php/
WORKDIR /var/www/html
