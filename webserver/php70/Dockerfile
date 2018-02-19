FROM php:7.0.10-fpm
ENV PHP_INI_DIR /usr/local/etc/php/
COPY customized.ini $PHP_INI_DIR/conf.d/customized.ini
COPY opcache.ini $PHP_INI_DIR/conf.d/opcache.ini

# php extension
RUN apt-get update -y && apt-get install -y htop cron nano libicu-dev \
    libmcrypt-dev libxml2-dev libxslt-dev libzip-dev libfreetype6-dev \
    libjpeg62-turbo-dev libpng12-dev \
    && docker-php-ext-install -j$(nproc) bcmath calendar \
    exif gettext intl mcrypt mysqli pcntl pdo_mysql soap \
    sockets wddx xsl zip \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd