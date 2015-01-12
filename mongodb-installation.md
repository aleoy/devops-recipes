# MongoDB on Ubuntu

## Installation through 10gen's (makers of mongodb) package repository

```sh
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 7F0CEB10
```
```sh
echo 'deb http://downloads-distro.mongodb.org/repo/ubuntu-upstart dist 10gen' | 
```
```sh
sudo tee /etc/apt/sources.list.d/mongodb.list
```
```sh
sudo apt-get update
```
```sh
sudo apt-get install -y mongodb-org
```

## Managing mongo server
```sh
sudo service mongod start
```
```sh
sudo service mongod stop
```
```sh
sudo service mongod restart
```



Intructions extrated from:
[Ubuntu installation](http://docs.mongodb.org/manual/tutorial/install-mongodb-on-ubuntu/?_ga=1.79284567.2127111810.1421055699)
[Production Notes](http://docs.mongodb.org/manual/administration/production-notes/)