# RHEL 6.2 install process for Plone

## Root user installs

```
yum install python27 libjpeg-devel libjpeg-turbo zlib-devel bzip2-devel openssl-devel xz-libs wget zlib-devel bzip2-devel patch openssl-devel libjpeg-devel libxslt-devel readline-devel make which python27.x86_64 python27-python-devel.x86_64 screen gcc g++ make tar gzip emacs svn git httpd openssl-devel libdb-devel cyrus-sasl-devel libpcre pcre-devel
useradd zope
yum install mod_ssl openssl
cd /etc/httpd/conf.d/
openssl genrsa -out ca.key 2048
openssl req -new -key ca.key -out ca.csr
openssl x509 -req -days 365 -in ca.csr -signkey ca.key -out ca.crt
cp ca.crt /etc/pki/tls/certs
cp ca.key /etc/pki/tls/private/ca.key
cp ca.csr /etc/pki/tls/private/ca.csr
emacs /etc/httpd/conf.d/ssl.conf
/etc/init.d/httpd restart
```

## Zope user installs

```
wget https://launchpad.net/plone/4.3/4.3.3/+download/Plone-4.3.3-UnifiedInstaller.tgz
tar xf Plone-4.3.3-UnifiedInstaller.tgz
wget http://www.python.org/ftp/python/2.7.9/Python-2.7.9.tar.xz
tar -xvf Python-2.7.9.tar.xz
cd Python-2.7.9
./configure --prefix=/home/zope/pythons/python-2.7.9
make
make altinstall
ln -s /home/zope/pythons/python-2.7.9/bin/python2.7 /home/zope/pythons/python-2.7.9/bin/python
emacs ~/.bash_profile
export EDITOR=emacs
cd Plone-4.3.3-UnifiedInstaller
./install.sh standalone --static-lxml=yes
```