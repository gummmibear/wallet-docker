# See https://github.com/docker-library/php/blob/4677ca134fe48d20c820a19becb99198824d78e3/7.0/fpm/Dockerfile
FROM php:7.1-fpm

RUN apt-get update && apt-get install -y \
    unzip \
    libssl-dev \
    libmcrypt-dev

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
RUN composer --version

# Set timezone
RUN rm /etc/localtime
RUN ln -s /usr/share/zoneinfo/Poland /etc/localtime
RUN "date"

# Type docker-php-ext-install to see available extensions
RUN docker-php-ext-install mcrypt bcmath pdo_mysql
RUN pecl install mongodb && \
    docker-php-ext-enable mongodb

#ENV PHPREDIS_VERSION 3.0.0

#RUN mkdir -p /usr/src/php/ext/redis \
#    && curl -L https://github.com/phpredis/phpredis/archive/$PHPREDIS_VERSION.tar.gz | tar xvz -C /usr/src/php/ext/redis --strip 1 \
#    && echo 'redis' >> /usr/src/php-available-exts \
#    && docker-php-ext-install redis

WORKDIR /var/www/wallet
