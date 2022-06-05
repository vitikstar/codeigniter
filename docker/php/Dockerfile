FROM debian:stretch

RUN apt-get update && apt-get install -y --no-install-recommends \
nano \
mc \
sudo \
    curl \
    wget \
    zip \
    git \
    unzip && \
    rm -rf /var/lib/apt/lists/* && \
    apt-get clean

# Install nginx
RUN apt-get update && apt-get -y install nginx && \
    echo "\ndaemon off;" >> /etc/nginx/nginx.conf && \
    rm -rf /etc/nginx/sites-enabled/*

# Install PHP
RUN apt-get install -y apt-transport-https lsb-release ca-certificates && \
    wget -O /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/apt.gpg && \
    echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list && \
    apt-get update && \
    apt-get install -y \
    php7.1 \
    php7.1-fpm

EXPOSE 80 443

CMD service php7.1-fpm start && nginx

# Install composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN composer self-update 1.6.0

RUN composer --version

# Install node
RUN curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.3/install.sh | bash
RUN bash -l -c "source /root/.bashrc"
RUN bash -l -c "nvm install v14.15.5"
RUN bash -l -c "nvm install lts/erbium"
RUN bash -l -c "nvm use v14.15.5"
RUN bash -l -c "node -v"
RUN bash -l -c "chmod -R 117 /root"

ARG UID
RUN addgroup --gid $UID --system app \
    && adduser --uid $UID --system --disabled-login --disabled-password --gid $UID app

ADD php.ini /usr/local/etc/php/conf.d/40-custom.ini

WORKDIR /var/www

CMD ["php-fpm"]