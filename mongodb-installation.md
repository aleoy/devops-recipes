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
## Setting up authentication
### Add user administrator.
```javascript
use admin
db.createUser(
  {
    user: "siteUserAdmin",
    pwd: "password",
    roles: [ { role: "userAdminAnyDatabase", db: "admin" } ]
  }
)
```
### Create a user administrator for a single database.
```javascript
use records
db.createUser(
  {
    user: "recordsUserAdmin",
    pwd: "password",
    roles: [ { role: "userAdmin", db: "records" } ]
  }
)
```
[source](http://docs.mongodb.org/manual/tutorial/add-user-administrator/)

## Create db users
### Connect to MongoDB with the appropriate privileges.
```sh
mongo --port 27017 -u siteUserAdmin -p password --authenticationDatabase admin
```
### Create the new user.
```javascript
use reporting
db.createUser(
    {
      user: "reportsUser",
      pwd: "12345678",
      roles: [
         { role: "read", db: "reporting" },
         { role: "read", db: "products" },
         { role: "read", db: "sales" },
         { role: "readWrite", db: "accounts" }
      ]
    }
)
```
[source](http://docs.mongodb.org/manual/tutorial/add-user-to-database/)

Intructions extrated from:
[Ubuntu installation](http://docs.mongodb.org/manual/tutorial/install-mongodb-on-ubuntu/?_ga=1.79284567.2127111810.1421055699)
[Production Notes](http://docs.mongodb.org/manual/administration/production-notes/)