FROM nginx

RUN apt-get update -qq && apt-get -y install apache2-utils
ENV RAILS_ROOT /var/www/rails_nginx_docker

WORKDIR $RAILS_ROOT
RUN mkdir log

COPY public public/
COPY docker/web/nginx.conf /tmp/docker_example.nginx

RUN envsubst '$RAILS_ROOT' < /tmp/docker_example.nginx > /etc/nginx/conf.d/default.conf
EXPOSE 80

CMD [ "nginx", "-g", "daemon off;" ]