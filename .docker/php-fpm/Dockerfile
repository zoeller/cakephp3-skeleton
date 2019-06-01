FROM php:7.3-fpm

ENV XDEBUG_VERSION 2.7.2
ENV MEMCACHED_VERSION 3.1.3

RUN apt-get update

# Enable the intl extension to use CakePHP
RUN apt-get install -y libicu-dev
RUN docker-php-ext-install intl

RUN docker-php-ext-enable opcache

RUN pecl install "xdebug-${XDEBUG_VERSION}"
RUN docker-php-ext-enable xdebug
RUN echo "xdebug.remote_enable=1" >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_autostart=1" >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_connect_back=0" >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_host=172.20.0.1" >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_port=10000" >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.idekey=PHPSTORM" >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.profiler_enable_trigger=1" >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.profiler_enable=0" >> /usr/local/etc/php/conf.d/xdebug.ini
