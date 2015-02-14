FROM alexisvincent/nginx:1.7.9
MAINTAINER Alexis Vincent <alexisjohnvincent@gmail.com>

ENV FPM_VERSION 5.4.36-0+deb7u3

RUN \
    apt-get update && \
    apt-get -y install php5-fpm=${FPM_VERSION} && \
    apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

# Add configs
COPY container/php_restrictions.conf /etc/nginx/global/php_restrictions.conf
COPY container/static_asset_caching.conf /etc/nginx/global/static_asset_caching.conf
COPY container/php-fpm.conf /etc/nginx/php-fpm.conf
COPY container/default.conf /etc/nginx/conf.d/default.conf

COPY container/supervisord.conf /etc/supervisor/conf.d/supervisord.conf

COPY container/index.php /data/www/index.php

# Container Config
CMD ["/usr/bin/supervisord"]
EXPOSE 80 443