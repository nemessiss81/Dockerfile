FROM webdevops/php:7.2

ENV WEB_DOCUMENT_ROOT=/app \
    WEB_DOCUMENT_INDEX=index.php \
    WEB_ALIAS_DOMAIN=*.vm \
    WEB_PHP_TIMEOUT=600 \
    WEB_PHP_SOCKET=""
ENV WEB_PHP_SOCKET=127.0.0.1:9000

COPY conf/ /opt/docker/

#add nginx
RUN wget http://nginx.org/keys/nginx_signing.key && \
  apt-key add nginx_signing.key && \
  echo "deb http://nginx.org/packages/mainline/debian/ stretch nginx" >>  /etc/apt/sources.list.d/nginx.list && \
  apt-get update

RUN set -x \
    # Install nginx
    && apt-install \
        nginx=1.15.8-1~stretch \
    && docker-run-bootstrap \
    && docker-image-cleanup

EXPOSE 80
