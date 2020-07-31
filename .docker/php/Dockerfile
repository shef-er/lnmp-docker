FROM php:7.4-fpm-alpine

ARG USER_ID
ARG GROUP_ID

RUN set -ex \
    && apk --no-cache add libzip-dev curl-dev libpng-dev libxslt-dev icu-dev

RUN pecl channel-update pecl.php.net

RUN set -ex \
    && apk add --no-cache --virtual .phpize-deps $PHPIZE_DEPS imagemagick-dev libtool \
    && export CFLAGS="$PHP_CFLAGS" CPPFLAGS="$PHP_CPPFLAGS" LDFLAGS="$PHP_LDFLAGS" \
    && pecl install imagick-3.4.4 \
    && docker-php-ext-enable imagick \
    && pecl install xdebug-2.9.6 \
    && docker-php-ext-enable xdebug \
    && apk add --no-cache --virtual .imagick-runtime-deps imagemagick \
    && apk del .phpize-deps

RUN set -ex \
    && apk --no-cache add curl oniguruma oniguruma-dev \
    && docker-php-ext-install pdo_mysql \
    && docker-php-ext-install curl \
    && docker-php-ext-install gd \
    && docker-php-ext-install mbstring \
    && docker-php-ext-install mysqli \
    && docker-php-ext-install json \
    && docker-php-ext-install xsl \
    && docker-php-ext-install intl \
    && docker-php-ext-install zip

RUN wget https://getcomposer.org/installer -O - -q \
    | php -- --install-dir=/bin --filename=composer --quiet

RUN apk --no-cache add shadow \
    && usermod -u ${USER_ID} www-data \
    && groupmod -g ${GROUP_ID} www-data

WORKDIR /var/www

USER "${USER_ID}:${GROUP_ID}"

EXPOSE 9000

CMD ["php-fpm"]
