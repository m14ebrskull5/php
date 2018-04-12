FROM centos

# /usr/local/php7/etc/php-fpm.conf
# /usr/local/php7/etc/php.ini
# /usr/local/php7/etc/php-fpm.d/microvcard.conf

RUN yum -y update \
    && yum install -y epel-release gcc zlib zlib-devel openssl gcc automake db4-devel libpng-devel libXpm-devel php-redis autoconf libtool make gcc-c++ curl curl-devel pcre-devel gmp-devel libmcrypt libmcrypt-devel zlib-devel openssl-devel vim which bzip2 bzip2-devel libjpeg libjpeg-devel libc-client-devel git  jemalloc pcre sqlite-devel sqlite supervisor gd gd-devel libxslt-devel htop nload libxml2 libxml2-devel php-gd freetype* lua lua-devel python34 python34-setuptools redis opencv-python wget  php-mcrypt\
WORKDIR ~
RUN wget http://cn2.php.net/distributions/php-7.1.11.tar.gz \
    && tar -xvf php-7.1.11.tar.gz \
    && cd php-7.1.11 \
    && ./configure --prefix=/usr/local/php7 \
    	--with-config-file-path=/usr/local/php7/etc \
    	--enable-fpm \
  		--enable-mbstring  \
  		--with-curl   --with-mcrypt  --with-openssl \
        --enable-inline-optimization --with-bz2  --with-zlib --enable-sockets \
        --enable-sysvsem --enable-sysvshm --enable-pcntl --enable-mbregex \
        --with-mhash --enable-zip --with-pcre-regex  --with-mysqli \
        --with-gd --with-jpeg-dir --with-jpeg-dir --with-freetype-dir  --with-pdo-mysql --with-mysql-sock=var/mysql/mysql.sock \
     && make && make install

ADD php-fpm.conf /usr/local/php7/etc/
ADD php.ini /usr/local/php7/etc/
ADD microvcard.conf /usr/local/php7/etc/
EXPOSE 9000

CMD ["/usr/local/php7/sbin/php-fpm"]