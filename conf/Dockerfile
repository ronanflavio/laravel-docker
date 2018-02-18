FROM php:7.2.2-cli-stretch

ADD sites-enabled /etc/apache2/sites-enabled

COPY php.ini /etc/php/7.2/apache2
COPY composer.phar /usr/local/bin/composer

RUN apt-get update -y
RUN apt-get install -y vim
RUN apt-get install -y git
RUN chmod 777 /usr/local/bin/composer
RUN composer self-update
