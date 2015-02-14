## Debian Dockerfile


This repository contains **Dockerfile** of [Debian](http://www.debian.org/) for [Docker](https://www.docker.com/)'s [automated build](https://registry.hub.docker.com/u/alexisvincent/debian/) published to the public [Docker Hub Registry](https://registry.hub.docker.com/).


### Base Docker Image

* [alexisvincent/debian:wheezy](https://registry.hub.docker.com/u/alexisvincent/debian/)


### Installation

1. Install [Docker](https://www.docker.com/).

2. Download [automated build](https://registry.hub.docker.com/u/alexisvincent/debian/) from public [Docker Hub Registry](https://registry.hub.docker.com/): `docker pull alexisvincent/debian`

   (alternatively, you can build an image from Dockerfile: `docker build -t="alexisvincent/debian" github.com/alexisvincent/docker-debian`)


### Usage

    docker run -it --rm alexisvincent/debian

### Example Docker File

    FROM alexisvincent/debian:wheezy
    MAINTAINER Alexis Vincent <alexisjohnvincent@gmail.com>
    
    ENV APACHE_VERSION 2.2.22-13+deb7u4
    ENV APACHE_RUN_USER www-data
    ENV APACHE_RUN_GROUP www-data
    ENV APACHE_LOG_DIR /var/log/apache2
    
    RUN \
        apt-get update && \
        apt-get -y install apache2=${APACHE_VERSION} && \
        apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
    
    COPY container/apache2.conf /etc/apache2/apache2.conf
    
    COPY container/000-default /etc/apache2/sites-enabled/000-default
    COPY container/000-default-ssl /etc/apache2/sites-enabled/001-default-ssl
    
    RUN a2enmod ssl rewrite
    
    EXPOSE 80
    EXPOSE 443
    
    CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]

