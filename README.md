# dcnmp-builder
![Docker Image CI](https://github.com/edenleung/dcnmp-builder/workflows/Docker%20Image%20CI/badge.svg)

PHP: 7.1 ~ 7.3 

* REDIS: 4.2.0
* SWOOLE: 4.5.2
* XDEBUG: 2.6.1

Support `pdo pdo_mysql mysqli pcntl exif bcmath calendar gmp sockets gettext shmop sysvmsg curl dba ldap mbstring gettext ftp bz2 opcache readline sysvsem sysvshm zip gd`, `composer`, `Xdebug`, `PgSql`, `Memcached`, `Redis`, `Swoole`

### workspace
`/var/www/html`

### usage
版本
* xiaodi93/dcnmp-php71
* xiaodi93/dcnmp-php72
* xiaodi93/dcnmp-php73

`latest`不含xdeug  
`debug` 含有xdeug
```docker
php71:
  image: xiaodi93/dcnmp-php71:latest
  
php71debug:
  image: xiaodi93/dcnmp-php71:debug
```
