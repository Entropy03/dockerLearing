FROM php7-zhq

ENV TZ=Asia/Shanghai


RUN set -xe \
    && echo "构建依赖" \
    && buildDeps=" \
        libpq-dev \
    " \
    && echo "安装 php 以及编译构建组件所需包" \
    && apt-get update \
    && apt-get install -y  ${buildDeps} --no-install-recommends \
    && echo "编译安装 php 组件" \
    && docker-php-ext-install  pdo_pgsql  pgsql  \
   
    && echo "清理" \
    && apt-get purge -y --auto-remove \
        -o APT::AutoRemove::RecommendsImportant=false \
        -o APT::AutoRemove::SuggestsImportant=false \
        $buildDeps \
    && rm -rf /var/cache/apt/* \
    && rm -rf /var/lib/apt/lists/*

COPY ./conf/php.conf /usr/local/etc/php/conf.d/php.conf