# dcnmp-builder
[![Build Status](https://travis-ci.org/xiaodit/dcnmp-builder.svg?branch=master)](https://travis-ci.org/xiaodit/dcnmp-builder)  
PHP: 7.1 ~ 7.3 

* REDIS: 4.2.0
* SWOOLE: 4.4.7
* XDEBUG: 2.6.1

support `bcmath pcntl pdo_mysql mysqli curl zip`, `composer`  

workspace `/var/www/html`

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
