FROM ccr.ccs.tencentyun.com/4-9-develop/php:init

RUN mkdir /var/www/html
# /usr/local/php7/etc/php-fpm.conf
# /usr/local/php7/etc/php.ini
# /usr/local/php7/etc/php-fpm.d/microvcard.conf
    
ADD php-fpm.conf /usr/local/php7/etc/
ADD php.ini /usr/local/php7/etc/
ADD microvcard.conf /usr/local/php7/etc/
ADD index.php /var/www/html
EXPOSE 9000

CMD ["/usr/local/php7/sbin/php-fpm"]