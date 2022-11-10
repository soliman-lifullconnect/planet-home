FROM bitnami/laravel:9.3.10

RUN mkdir planet-home
WORKDIR /planet-home


## add non-root user
RUN chown -R $USER:$USER /planet-home


RUN bundle install


RUN . /planet-home