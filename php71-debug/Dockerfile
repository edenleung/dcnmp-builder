ARG PHP_VERSION=7.1
ARG PHP_SWOOLE=4.4.7
ARG PHP_XDEBUG=2.6.1
ARG PHP_REDIS=4.2.0
ARG PHP_MEMCACHED=3.1.3
ARG PHP_PDO_SQLSRV=5.6.1

FROM php:${PHP_VERSION}-fpm-alpine

#阿里云源
RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g' /etc/apk/repositories
RUN apk add --no-cache autoconf g++ libtool make curl-dev libxml2-dev linux-headers libzip-dev

RUN docker-php-ext-install bcmath pcntl pdo_mysql mysqli curl zip

#Composer
RUN curl -sS https://getcomposer.org/installer | php \
     && mv composer.phar /usr/local/bin/composer \
     && composer self-update --clean-backups \
     && composer config -g repo.packagist composer https://mirrors.aliyun.com/composer/

#GD
RUN apk add --no-cache freetype-dev libjpeg-turbo-dev libpng-dev \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install ${MC} gd

#Swoole
RUN if [ ${PHP_SWOOLE} != false ]; then \
    curl -O http://pecl.php.net/get/swoole-${PHP_SWOOLE}.tgz -L \
    && (tar -zxvf swoole-${PHP_SWOOLE}.tgz && cd swoole-${PHP_SWOOLE} && phpize && ./configure --enable-openssl && make && make install) \
    && docker-php-ext-enable swoole \
;fi

# XDEBUG
ARG PHP_XDEBUG=false
RUN if [ ${PHP_XDEBUG} != false ]; then \
    curl -O http://pecl.php.net/get/xdebug-${PHP_XDEBUG}.tgz -L \
    && pecl install xdebug-${PHP_XDEBUG}.tgz \
    && docker-php-ext-enable xdebug \
;fi

# REDIS
ARG PHP_REDIS=false
RUN if [ ${PHP_REDIS} != false ]; then \
    curl -O http://pecl.php.net/get/redis-${PHP_REDIS}.tgz -L \
    && pecl install redis-${PHP_REDIS}.tgz \
    && docker-php-ext-enable redis \
;fi
# MEMCACHED
ARG PHP_MEMCACHED=false
RUN if [ ${PHP_MEMCACHED} != false ]; then \
    curl -O http://pecl.php.net/get/memcached-${PHP_MEMCACHED}.tgz -L \
    && pecl install memcached-${PHP_MEMCACHED}.tgz \
    && docker-php-ext-enable memcached \
;fi

#PHP_PDO_SQLSRV
ARG PHP_PDO_SQLSRV=false
RUN if [ ${PHP_PDO_SQLSRV} != false ]; then \
    curl -O http://pecl.php.net/get/pdo_sqlsrv-${PHP_PDO_SQLSRV}.tgz -L \
    && pecl install pdo_sqlsrv-${PHP_PDO_SQLSRV}.tgz \
    && docker-php-ext-enable pdo_sqlsrv \
;fi

WORKDIR /var/www/html
