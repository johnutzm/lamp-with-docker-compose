FROM php:7.0-fpm

RUN apt-get update && apt-get install -y \
        git \
        libcurl4-openssl-dev \
        libfreetype6-dev \
        libicu-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng12-dev \
        zlib1g-dev \
    && rm -rf /var/lib/apt/lists/* \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) \
        curl \
        gd \
        iconv \
        intl \
        mbstring \
        mcrypt \
        pdo_mysql \
        zip

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer \
    && composer global require --prefer-dist \
        phpunit/phpunit \
        phpmd/phpmd \
        squizlabs/php_codesniffer \
    && echo "export PATH=~/.composer/vendor/bin:$PATH" >> ~/.bash_profile
