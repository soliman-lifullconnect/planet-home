FROM bitnami/laravel:9.3.10

RUN mkdir planet-home

RUN apt-get update && apt-get install -y \
    git \
    curl \
    libpng-dev \
    libonig-dev \
    libxml2-dev \
    zip \
    unzip\
    nano


WORKDIR /planet-home
## add non-root user
RUN chown -R $USER:$USER /planet-home


# RUN bundle install


RUN . /planet-home