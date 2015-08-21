# Ubuntu 14.04 LTS install process for Plone

## Root user installs

```
apt-get update
apt-get dist-upgrade
apt-get install libreadline5 libreadline5-dev zlib1g zlib1g-dev libjpeg62 libjpeg62-dev libssl0.9.8 \
libssl-dev build-essential subversion cron groff-base wget lynx apache2

apt-get install postfix
apt-get install emacs
apt-get install wv xpdf-utils
apt-get install pkg-config libpcre3 libpcre3-dev
apt-get install libxml2-dev libxslt1-dev
apt-get install libgeos-c1 libgeos-dev
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
```