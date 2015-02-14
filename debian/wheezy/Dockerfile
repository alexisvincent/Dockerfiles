#
# Debian Dockerfile
#
# https://github.com/alexisvincent/Dockerfiles/debian
#

# Pull base image.
FROM debian:wheezy

MAINTAINER Alexis Vincent "alexisjohnvincent@gmail.com"

# Install.
RUN \
  apt-get update && \
  apt-get install -y git wget supervisor && \
  apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

# Set environment variables.
ENV HOME /root

# Define working directory.
WORKDIR /root

# Define default command.
CMD ["bash"]