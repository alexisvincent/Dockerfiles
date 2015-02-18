FROM alexisvincent/nginx.php:5.4.36
MAINTAINER <alexisjohnvincent@gmail.com>

# Install.
RUN \
  apt-get update && \
  apt-get install -y php5-mysql php5-gd libfreetype6 cron exim4 && \
  apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

COPY container/default.conf /etc/nginx/conf.d/default.conf
COPY container/supervisord.conf /etc/supervisor/conf.d/supervisord.conf

COPY container/cron.sh /data/cron.sh
RUN chmod o+x /data/cron.sh

RUN rm -rf /data/www/*
# ADD src /data/www