FROM ubuntu/apache2
ENV TZ=Europe/Kiev
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

RUN apt-get update && apt-get install -y \
    nano \
    software-properties-common \
    mc \
    sudo \
    curl \
    wget \
    zip \
    git \
    unzip && \
    rm -rf /var/lib/apt/lists/* && \
    apt-get clean

RUN sudo apt-get update && apt-get install -y mariadb-server



RUN apt-get update && apt-get  install -y php \
    php-cli \
    php-fpm \
    php-json \
    php-common \
    php-mysql \
    php-zip \
    php-gd \
    php-mbstring \
    php-curl \
    php-xml \
    php-xsl \
    php-pear \  
    php-bcmath

RUN sudo a2enmod rewrite
RUN sudo service apache2 restart



WORKDIR /var/www

