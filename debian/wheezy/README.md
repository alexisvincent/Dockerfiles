## Debian Dockerfile


This repository contains **Dockerfile** of [Debian](http://www.debian.org/) for [Docker](https://www.docker.com/)'s [automated build](https://registry.hub.docker.com/u/alexisvincent/debian/) published to the public [Docker Hub Registry](https://registry.hub.docker.com/).


### Base Docker Image

* [debian:wheezy](https://registry.hub.docker.com/u/alexisvincent/debian/)


### Installation

1. Install [Docker](https://www.docker.com/).

2. Download [automated build](https://registry.hub.docker.com/u/alexisvincent/debian/) from public [Docker Hub Registry](https://registry.hub.docker.com/): `docker pull alexisvincent/debian`

   (alternatively, you can build an image from Dockerfile: 'docker build -t="alexisvincent/debian" github.com/alexisvincent/Dockerfiles/debian')

### Usage

    docker run -it --rm alexisvincent/debian
