FROM ubuntu:16.04
FROM python:3.6

maintainer mathpresso

# use mirror
RUN cd /etc/apt && \
  sed -i 's/deb.debian.org/ftp.daum.net/g' sources.list

# install nginx
RUN \
  apt-get update && \
  apt-get install -y nginx && \
  rm -rf /var/lib/apt/lists/* && \
  echo "\ndaemon off;" >> /etc/nginx/nginx.conf && \
  rm /etc/nginx/sites-enabled/default && \
  chown -R www-data:www-data /var/lib/nginx

# install some packages for python/django/nginx/supervisor
RUN apt-get update
RUN apt-get install -y build-essential git
RUN apt-get install -y python python-dev python-setuptools

# install mysql_config
RUN apt-get install -y default-libmysqlclient-dev

# install supervisor
RUN apt-get install -y supervisor

# install uwsgi
RUN apt-get install -y python3-pip
RUN pip3 install uwsgi

# install phantomJS
RUN apt-get -y install build-essential chrpath libssl-dev libxft-dev libfreetype6 libfreetype6-dev libfontconfig1 libfontconfig1-dev
RUN wget -q https://bitbucket.org/ariya/phantomjs/downloads/phantomjs-2.1.1-linux-i686.tar.bz2 -O phantomjs-2.1.1-linux-i686.tar.bz2
RUN tar xvjf phantomjs-2.1.1-linux-i686.tar.bz2

RUN mv -f phantomjs-2.1.1-linux-i686 /usr/local/share/
RUN ln -sf /usr/local/share/phantomjs-2.1.1-linux-i686/bin/phantomjs /usr/local/share/phantomjs
RUN ln -sf /usr/local/share/phantomjs-2.1.1-linux-i686/bin/phantomjs /usr/local/bin/phantomjs
RUN ln -sf /usr/local/share/phantomjs-2.1.1-linux-i686/bin/phantomjs /usr/bin/phantomjs

# install ffmpeg
RUN apt-get install -y ffmpeg
