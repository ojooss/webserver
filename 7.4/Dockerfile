FROM php:7.4-apache

# --------------------------------------------------------------
# initially update debian packages
# --------------------------------------------------------------
RUN DEBIAN_FRONTEND=noninteractive apt-get update
RUN DEBIAN_FRONTEND=noninteractive apt-get upgrade -y


# --------------------------------------------------------------
# add composer
# --------------------------------------------------------------
COPY --from=composer:1 /usr/bin/composer /usr/local/bin/composer_v1
COPY --from=composer /usr/bin/composer /usr/local/bin/composer


# --------------------------------------------------------------
# add PHP packages
# --------------------------------------------------------------
RUN DEBIAN_FRONTEND=noninteractive apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng-dev \
        libxml2-dev \
        libxslt-dev \
        zlib1g-dev \
        libzip-dev \
        libcurl4-openssl-dev \
        libssl-dev \
        pkg-config \
        git \
		zip \
		unzip \
    && apt-get clean \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) gd \
    && docker-php-ext-install zip \
    && docker-php-ext-install bcmath \
    && docker-php-ext-install sockets \
    && docker-php-ext-install intl \
    && docker-php-ext-install mysqli \
    && docker-php-ext-install pdo_mysql \
    && pecl install mongodb && docker-php-ext-enable mongodb \
    && pecl install xdebug && docker-php-ext-enable xdebug


# --------------------------------------------------------------
# add imagemagick and ghostscript
# --------------------------------------------------------------
# from: https://pecl.php.net/package/imagick
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends \
    libmagickwand-dev libmagickcore-dev ghostscript \
    && apt-get clean \
    && pecl install imagick-3.4.3 \
    && docker-php-ext-enable imagick


# --------------------------------------------------------------
# add node.js and yarn
# --------------------------------------------------------------
RUN DEBIAN_FRONTEND=noninteractive apt-get update \
    && DEBIAN_FRONTEND=noninteractive apt-get install apt-transport-https gnupg2 gcc g++ make -y \
    && apt-get clean \
    && curl -fsSL https://deb.nodesource.com/setup_14.x | bash - \
    && curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add -  \
    && echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list \
    && DEBIAN_FRONTEND=noninteractive apt-get update -y \
    && DEBIAN_FRONTEND=noninteractive apt-get install  -y nodejs yarn


# --------------------------------------------------------------
# set timezoneg
# --------------------------------------------------------------
ARG timezone='Europe/Berlin'
RUN echo "date.timezone="$timezone > /usr/local/etc/php/conf.d/date_timezone.ini


# --------------------------------------------------------------
# activate apache modules
# --------------------------------------------------------------
RUN a2enmod headers && \
    a2enmod rewrite && \
    a2enmod ssl && \
    a2enmod proxy && \
    a2enmod proxy_http
