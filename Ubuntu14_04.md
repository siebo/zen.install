# Ubuntu 14.04 LTS install process for Plone

## Root user installs
```
apt-get update
apt-get dist-upgrade
apt-get install libreadline-gplv2-dev zlib1g zlib1g-dev libjpeg62 \
libjpeg62-dev libssl0.9.8  libssl-dev build-essential subversion \
cron groff-base wget lynx apache2 wv xpdf-utils libxml2-dev libxslt1-dev 

a2enmod rewrite proxy proxy_http
/etc/init.d/apache2 restart
```

## If you're running Varnish
```
apt-get install pkg-config libpcre3 libpcre3-dev
```

## If you're running collective.geo
```
apt-get install libgeos-c1 libgeos-dev libgeos-dev
```

## Text editor of your choice
```
apt-get install emacs
```

## MTA/mailserver of your choice
```
apt-get install postfix
```

## Adding a user under which to run zope
```
useradd -d /home/zope -m zope
passwd zope
```

## Changing the default shell for the zope user

```
chsh -s /bin/bash zope
```

## Zope user installs

```
mkdir pythons downloads
cd ~/downloads
wget http://www.python.org/ftp/python/2.7.10/Python-2.7.10.tgz 
tar xzf Python-2.7.10.tgz 
cd Python-2.7.10 
./configure --prefix=/home/zope/pythons/python-2.7.10 
make 
make altinstall
ln -s /home/zope/pythons/python-2.7.10/bin/python2.7.10 /home/zope/pythons/python-2.7.10/bin/python
```

## Make our new python the default 
```
emacs ~/.bash_profile
```

## There we add:
```
export PATH=/home/zope/pythons/python-2.7.10/bin:$PATH
```
