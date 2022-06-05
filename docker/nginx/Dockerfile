FROM ubuntu:20.04
SHELL ["/bin/sh", "-c"]
ENV TZ=Europe/Kiev
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
RUN apt-get update && apt-get install -y  sed \
    mc \
    apt-utils \
    sudo \
    curl \
    wget \
    zip \
    git \
    software-properties-common \
    unzip
RUN rm -rf /var/lib/apt/lists/* 
RUN apt-get clean
    
RUN sudo apt-get update && apt-get install -y mariadb-server


RUN apt-get update && apt-get  install -y php-cli \
    php-fpm \
    php-json \
    php-common \
    php-mysql \
    php-zip \
    php-gd \
    php-mbstring \
    php-curl \
    php-intl \
    php-xml \
    php-xsl \
    php-pear \ 
    php-xsl \  
    php-bcmath \
    php-pdo



RUN apt-get update && apt-get install -y nginx \
 php7.4-fpm

ENV COMPOSER_ALLOW_SUPERUSER = 1
ENV MYSQL_ROOT_PASSWORD = 'root'

RUN sudo adduser docker
RUN sudo su - docker
RUN rm -rf vendor/



# RUN sudo ln -s /etc/nginx/sites-available/default /etc/nginx/sites-enabled/

# ADD php.ini /usr/local/etc/php/conf.d/40-custom.ini
CMD service php7.4-fpm start && nginx -g "daemon off;"



# RUN /etc/init.d/ service --status-all

EXPOSE 80

WORKDIR /var/www

