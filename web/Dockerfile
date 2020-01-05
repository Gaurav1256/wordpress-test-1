FROM ubuntu:16.04

RUN apt-get update -y
RUN apt-get install -y software-properties-common

RUN apt-get install -y python-software-properties
RUN LC_ALL=C.UTF-8 add-apt-repository -y ppa:ondrej/php
RUN apt-get update -y
RUN apt-get install apache2 -y
COPY config/apache2.conf /etc/apache2/apache2.conf
RUN apt-get install -y php7.1
RUN apt-get install -y php7.1-xml php7.1-mbstring php7.1-mysqli php7.1-intl php7.1-gd php7.1-mysql php7.1-zip php7.1-mcrypt php7.1-soap php7.1-fpm php7.1-curl php7.1-bcmath 
RUN a2enmod rewrite
RUN service apache2 restart
COPY htdocs/ /var/www/html/
RUN apt-get install supervisor -y
COPY config/supervisord.conf /etc/supervisor/conf.d/
CMD ["/usr/bin/supervisord", "-n"]
#RUN apt-get update
WORKDIR /var/www/html
