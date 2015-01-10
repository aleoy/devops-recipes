#composer
curl -s http://getcomposer.org/installer | php
sudo mv composer.phar /usr/local/bin/composer

composer global require "fxp/composer-asset-plugin:1.0.0-beta4"

cd /var/www/

composer create-project --prefer-dist --stability=dev yiisoft/yii2-app-advanced example.com

cd example.com

chmod +x init

./init

composer require --dev "codeception/codeception: *" "codeception/specify: *" "codeception/verify: *"

composer require "fzaninotto/faker:*"

echo 'alias cept="/vagrant/yii2-base/vendor/bin/codecept"' >> ~/.profile

source ~/.profile


#on $APP_ROOT
cept bootstrap
cept build

edit edit tests/acceptance.suite.yml
set url accordingly for integration tests