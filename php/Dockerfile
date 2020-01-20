FROM amazonlinux:2

ENV TERM xterm
ENV LANG en_US.UTF-8
ENV PS1 "[\u@\h \W] $ "
WORKDIR /var/www/html/
RUN yum -y update
RUN yum -y install vim yum-utils zip unzip
RUN yum -y install httpd
RUN yum -y install wget
RUN wget https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
RUN wget http://rpms.remirepo.net/enterprise/remi-release-7.rpm
RUN rpm -Uvh remi-release-7.rpm epel-release-latest-7.noarch.rpm
RUN yum -y install php73-php
RUN yum -y install php73-php-gd 
RUN yum -y install php73-php-intl
RUN yum -y install php73-php-mbstring
RUN yum -y install php73-php-mysqlnd 
RUN yum -y install php73-php-xml
RUN yum -y install php73-php-zip
RUN yum -y install php73-php-posix
RUN yum -y install php73-php-pecl-memcached
RUN yum -y install php73-php-pecl-mcrypt
RUN yum -y install php73-php-devel php73-php-pear
RUN yum -y install gcc gcc-c++ pecl
RUN yum -y install nodejs npm --enablerepo=epel
RUN ln -s /usr/bin/php73 /usr/bin/php
RUN cd ~
RUN curl -sS https://getcomposer.org/installer | php
RUN mv composer.phar /usr/local/bin/composer
RUN ln -s /usr/local/bin/composer /usr/bin/composer
RUN yum -y install libXext
RUN yum -y install libXrender
RUN yum -y install xorg-x11-fonts-Type1
RUN yum -y install xorg-x11-fonts-misc
RUN yum -y install xorg-x11-fonts-75dpi
RUN yum -y install xorg-x11-fonts-100dpi
RUN yum -y install wine-ms-sans-serif-fonts
COPY file/virtualhost2.conf /etc/httpd/conf.d/virtualhost.conf

EXPOSE 80 443

RUN systemctl enable httpd

CMD ["/usr/sbin/httpd","-DFOREGROUND"]
