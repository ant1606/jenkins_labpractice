FROM php:8.1-apache

# 1. Install development packages and clean up apt cache.
RUN apt-get update && apt-get install -y \
  curl \
  g++ \
  git \
  libbz2-dev \
  libfreetype6-dev \
  libicu-dev \
  libjpeg-dev \
  libmcrypt-dev \
  libpng-dev \
  libreadline-dev \
  sudo \
  unzip \
  zip \
  && rm -rf /var/lib/apt/lists/*

# 2. Apache configs + document root.
#RUN echo "ServerName laravel-app.local" >> /etc/apache2/apache2.conf
ENV APACHE_DOCUMENT_ROOT=/var/www/html/public

# 6. We need a user with the same UID/GID as the host user
# MacOS staff group's gid is 20, so is the dialout group in alpine linux. We're not using it, let's just remove it.
RUN delgroup dialout

COPY . /var/www/html/
WORKDIR /var/www/html/
# RUN rm ./.editorconfig ./.env.development ./.env.example ./.env.production ./.phpunit.result.cache ./docker-compose.prod.yml ./docker-compose.yml ./phpunit.xml ./README.md



### VERSION DEL CURSO, NO FUNCIONABA
# FROM php:7.1.17-apache

# RUN a2enmod rewrite

# RUN apt-get update && apt-get install -y \
#   zlib1g-dev \
#   libicu-dev \
#   libxml2-dev \
#   libpq-dev\
#   && docker-php-ext-configure pgsql -with-pgsql=/usr/local/pgsql \
#   && docker-php-ext-install pdo pdo_mysql pdo_pgsql zip intl xmlrpc soap opcache \
#   && docker-php-ext-configure pdo_mysql --with-pdo-mysql=mysqlnd \
#   && apt-get install vim -y

# COPY  . /var/www/html/
# WORKDIR /var/www/html/
