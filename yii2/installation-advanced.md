# Yii2 Advanced app setup

This recipe assume that you have the following ingredients:
Ubuntu/trusty thar running on vagrant


## setting up composer

```sh
curl -s http://getcomposer.org/installer | php
```

```sh
sudo mv composer.phar /usr/local/bin/composer
```

```sh
composer global require "fxp/composer-asset-plugin:1.0.0-beta4"
```

```sh
cd /vagrant
```

```sh
composer create-project --prefer-dist --stability=dev yiisoft/yii2-app-advanced yii2app
```

```sh
cd yii2app
```

```sh
chmod +x init
```

```sh
./init
```

```sh
composer require --dev "codeception/codeception: *" "codeception/specify: *" "codeception/verify: *"
```

```sh
echo 'alias cept="/vagrant/yii2app/vendor/bin/codecept"' >> ~/.profile
```

```sh
source ~/.profile
```