FROM phpmyadmin/phpmyadmin

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

ENV PMA_HOST=mysql
ENV PMA_USER=root
ENV PMA_PASSWORD=root