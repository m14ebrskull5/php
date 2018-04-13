FROM php:7.0-fpm

RUN yum -y install freetype-devel libpng-devel libjpeg-devel \ 
docker-php-ext-configure gd --with-freetype-dir=/usr/include/ \
--with-jpeg-dir=/usr/include/

ADD index.php /var/www/html
EXPOSE 9000

CMD ["php-fpm"]