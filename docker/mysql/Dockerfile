FROM mariadb:10.3
SHELL ["/bin/sh", "-c"]
ENV TZ=Europe/Kiev
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
RUN apt-get update && apt-get install -y  nano \
    mc \
    sudo \
    curl \
    wget \
    zip \
    git \
    software-properties-common \
    unzip && \
    rm -rf /var/lib/apt/lists/* && \
    apt-get clean

# CMD sudo /etc/init.d/mysql restart;
# CMD sudo mysqldump -uroot -proot ems<'/var/ems.sql'
# CMD sudo  mysqldump -uroot -proot ems_edu<'/var/ems_edu.sql'
# CMD sudo mysqldump -uroot -proot main<'/var/main.sql'