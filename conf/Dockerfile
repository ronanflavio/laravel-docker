FROM ubuntu:xenial

ENV LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8 LANGUAGE=en_US.UTF-8

RUN apt-get update -y
RUN apt-get install -y apache2 zip nano
RUN apt-get install -y python-software-properties software-properties-common locales
RUN locale-gen en_US.UTF-8
RUN add-apt-repository ppa:ondrej/php -y
RUN apt-get update -y
RUN apt-get install -y php7.2 php-pear php7.2-curl php7.2-dev php7.2-gd php7.2-mbstring php7.2-zip php7.2-mysql php7.2-xml
RUN apt-get install -y vim
RUN apt-get install -y git
RUN echo "<?php phpinfo() ?>" > /var/www/html/info.php

ADD sites-enabled /etc/apache2/sites-enabled
COPY php.ini /etc/php/7.2/apache2
COPY composer.phar /usr/local/bin/composer

RUN chmod 777 /usr/local/bin/composer
RUN composer self-update

ENTRYPOINT ["/bin/bash", "-c", "a2enmod rewrite && service apache2 restart && tail -f /dev/null"]
