FROM php:7.2-fpm

RUN apt-get update && apt-get install -y \
		libfreetype6-dev \
		libjpeg62-turbo-dev \
		libmcrypt-dev \
		libpng-dev \
		python-opencv \
		python-numpy  \
		wget \
		git \
	&& curl -O https://getcomposer.org/composer.phar \
	&& mv composer.phar composer \
	&& mv composer /usr/local/bin \
	&& chmod +x /usr/local/bin/composer \
	&& docker-php-ext-install -j$(nproc) iconv mcrypt pdomysql\
	&& docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
	&& docker-php-ext-install -j$(nproc) gd \
	&& ln /dev/null /dev/raw1394 

WORKDIR /var/www/html
RUN composer create-project --prefer-dist laravel/laravel blog 5.5.*

EXPOSE 9000

CMD ["php-fpm"]