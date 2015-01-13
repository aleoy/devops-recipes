#assuming OS ubuntu/trusty64
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install -y nginx git
sudo apt-get install -y nginx git build-essential libfcgi-dev libfcgi0ldbl libjpeg62-dbg libmcrypt-dev libssl-dev libc-client2007e libc-client2007e-dev icu-devtools icu-doc libicu-dev libicu52 libicu52-dbg
sudo apt-get build-dep php5
wget -O php-5.6.4.tar.gz http://lv1.php.net/get/php-5.6.4.tar.gz/from/this/mirror
sudo mkdir -p /opt/php-5.6.4
cd php-5.6.4
sudo ln -s /usr/lib/libc-client.a /usr/lib/x86_64-linux-gnu/libc-client.a
./configure \
--prefix=/opt/php-5.6.4 \
--with-pdo-pgsql \
--with-zlib-dir \
--with-freetype-dir \
--enable-mbstring \
--with-libxml-dir=/usr \
--enable-soap \
--enable-calendar \
--with-curl \
--with-mcrypt \
--with-zlib \
--with-gd \
--with-pgsql \
--disable-rpath \
--enable-inline-optimization \
--with-bz2 \
--with-zlib \
--enable-sockets \
--enable-sysvsem \
--enable-sysvshm \
--enable-pcntl \
--enable-mbregex \
--with-mhash \
--enable-zip \
--with-pcre-regex \
--with-mysql \
--with-pdo-mysql \
--with-mysqli \
--with-png-dir=/usr \
--enable-gd-native-ttf \
--with-openssl \
--with-fpm-user=nginx \
--with-fpm-group=nginx \
--with-libdir=lib \
--enable-ftp \
--with-imap \
--with-imap-ssl \
--with-kerberos \
--with-gettext \
--with-gd \
--with-jpeg-dir=/usr/lib/ \
--enable-fpm \
--with-fpm-user=www-data \
--with-fpm-group=www-data

make

sudo make install

sudo cp sapi/fpm/php-fpm.conf /opt/php-5.6.4/etc/php-fpm.conf
sudo cp php.ini-production /opt/php-5.6.4/lib/php.ini


sudo vi /opt/php-5.6.4/etc/php-fpm.conf

[...]
pid = run/php-fpm.pid
[...]
user = www-data
group = www-data
[...]
listen = 127.0.0.1:9000
[...]
#include=/opt/php-5.6/etc/pool.d/*.conf

sudo cp sapi/fpm/init.d.php-fpm /etc/init.d/php-fpm

sudo chmod 755 /etc/init.d/php5.6.4-fpm

sudo /etc/init.d/php5.6.4-fpm start

#include php bin in .profile
echo 'PATH="/opt/php-5.6.4/bin:$PATH"' >> ~/.profile
source ~/.profile

sudo cp /etc/nginx/sites-available/default /etc/nginx/sites-available/example.com

sudo ln -s /etc/nginx/sites-available/example.com /etc/nginx/sites-enabled/example.com