# docker mariadb

See the reference [使用dokcer 构建 mariadb 数据库](http://dockone.io/article/2380)

## setup the mariadb container

``` shell
mkdir -p /data/mysql/data
chcon -Rt svirt_sandbox_file_t /data/mysql/data
docker run --privileged -v /data/mysql/data:/var/lib/mysql -p 4444:3306 -e MYSQL_ROOT_PASSWORD=root --name mariadb -d mariadb:latest

```
If not root user, it must uses `--privileged` parameter to obtain root privilege.

## use the mariadb

``` shell
docker exec -it mariadb bash
root@XXXX:/# mysql -uroot -proot
Welcome to the MariaDB monitor. Commands end with ; or \g.
Your MariaDB connection id is 3
Server version: 10.1.19-MariaDB-1~jessie mariadb.org binary distribution

Copyright (c) 2000, 2016, Oracle, MariaDB Corporation Ab and others.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [(none)]> show databases;
```

## use the mysql client

``` shell
mysql -uroot -p -h127.0.0.1 -P 4444
```
It must use `-h` parameter.
