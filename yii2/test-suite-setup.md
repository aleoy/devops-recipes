# Test suite setup

The test suite setup becomes much more clear by looking at the test documentation within the source repository
[yii2 repository doc](https://github.com/yiisoft/yii2/tree/master/apps/advanced/tests)

## Recipe

$APP_ROOT denotes the root folder of the application

### Preping codeception
```sh
cd $APP_ROOT

composer global require "codeception/codeception=2.0.*" "codeception/specify=*" "codeception/verify=*"

composer require --dev yiisoft/yii2-faker:*
```

### Setting configuration data

1 - Edit the common config file of the main application and setup the db connection information.
```sh
$APP_ROOT/common/config/main-local.php
```

2 - Edit codeception configuration and make the database connection point to the test database.
```sh
$APP_ROOT/tests/codeception/config/config.php
```

3 - Run the app migration.
```sh
chmod +x $APP_ROOT/yii
$APP_ROOT/yii migrate
```

4 - Run test migration
```sh
chmod +x $APP_ROOT/tests/codeception/bin/yii
$APP_ROOT/tests/codeception/bin/yii migrate
```

From now on the path of the file to be edited will contain the path branch "frontend", this is due to the fact that yii2 advanced application makes two separate applications "backend" and "frontend" sharing some common code and configuration (folder "common").

The following steps will handle the "frontend" test suite, in order to setup the "backend" the same steps from now on should be performed againg once the partial path has been changed to point to the "backend" *(steps 5-7)*

5 - Build the test suite
```sh
cd $APP_ROOT/tests/codeception/frontend
cept build
```

6 - Edit the acceptance.suite.yml and set the url where your server is running.
```sh
$APP_ROOT/tests/codeception/frontend/acceptance.suite.yml
```

7 - Edit codeception.yml and set the url where your server is running and append at the end the test entry script "index-test.php".
```sh
$APP_ROOT/tests/codeception/frontend/codeception.yml
```

8 - Running tests
```sh
cd $APP_ROOT/tests/codeception/frontend
cept run
```