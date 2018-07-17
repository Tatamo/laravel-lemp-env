FROM php:7.2.7

RUN apt-get update && \
    apt-get install -y \
    zip unzip git

# install composer
RUN curl -s http://getcomposer.org/installer | php && \
    mv composer.phar /usr/local/bin/composer
ENV COMPOSER_ALLOW_SUPERUSER=1 \
    COMPOSER_NO_INTERACTION=1
WORKDIR /var/www/laravel

# install nvm&node&npm
ARG NODE_VERSION=stable
RUN curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.11/install.sh | bash && \
    . $HOME/.bashrc && \
    nvm install $NODE_VERSION && \
    nvm use $NODE_VERSION && \
    npm install -g npm

