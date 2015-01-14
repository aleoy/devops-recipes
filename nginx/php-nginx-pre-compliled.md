sudo apt-get update
sudo apt-get -y upgrade
sudo apt-get install -y php5-cgi php5-fpm php5-mcrypt php5-curl php5-json php5-apcu php5-geoip php5-imagick php5-imap php5-intl php5-mongo php5-oauth php5-mysql
sudo php5enmod mcrypt curl json apcu geoip imagick imap intl mongo oauth mysql
sudo apt-get install -y nginx
sudo sed -i 's/user www-data/user vagrant/' /etc/nginx/nginx.conf
sudo sed -i 's/user = www-data/user = vagrant/' /etc/php5/fpm/pool.d/www.conf
sudo sed -i 's/group = www-data/group = vagrant/' /etc/php5/fpm/pool.d/www.conf
sudo sed -i 's/listen.owner = www-data/listen.owner =  vagrant/' /etc/php5/fpm/pool.d/www.conf
sudo sed -i 's/listen.group = www-data/listen.group =  vagrant/' /etc/php5/fpm/pool.d/www.conf
sudo sed -i 's/listen = \/var\/run\/php5-fpm.sock/listen = 127.0.0.1:9000/' /etc/php5/fpm/pool.d/www.conf
sudo service php5-fpm restart
sudo service nginx restart
sudo curl https://raw.githubusercontent.com/aleoy/devops-recipes/master/nginx/yii2app-site > yii2app-site ; sudo mv yii2app-site /etc/nginx/sites-available/yii2app-site
sudo ln -s /etc/nginx/sites-available/yii2app-site /etc/nginx/sites-enabled/yii2app-site


edit /etc/hosts

add following entries
127.0.0.1 yii2app
127.0.0.1 admin.yii2app
127.0.0.1 test.yii2app