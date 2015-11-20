# MAMP Config

A way to configure MAMP and keep the settings across MAMP upgrades.

## Prerequisites

Download and install MAMP - you don't need MAMP Pro, just regular MAMP.

## Installation

Clone this repo into `~/mamp` .

### Htdocs

```bash
cd /Applications/MAMP
mv /Applications/MAMP/htdocs htdocs.orig
ln -s ~/mamp/htdocs htdocs
```

### MySQL conf

```bash
cd /Applications/MAMP/conf
ln -s ~/mamp/mysql_conf/my.cnf my.cnf
```


### Apache conf

```bash
cd /Applications/MAMP/conf
mv apache apache.orig
ln -s ~/mamp/apache_conf apache
```

MAMP overwrites httpd.conf each restart so we need to symlink the whole folder rather than the httpd.conf file, which will be overwritten.


### Apache httpd.conf vhosts

Inside httpd.conf, make sure:

```apache
# Virtual hosts.
# You may need to replace ~/mamp with the absolute dir name.
Include ~/mamp/apache_conf/vhosts/*.conf
```


### PHP conf

```bash
cd /Applications/MAMP/bin/php
cd php5.6.7
mv conf conf.orig
# Do this for all versions of PHP you are using.
ln -s ~/mamp/php_conf/php5.6.7_conf conf
```

MAMP overwrites php.ini each restart / reconfig, so we need to symlink the whole conf folder rather than the php.ini file, which will be overwritten.


