# Ruby Base image:
FROM ruby:2.6.3-stretch

RUN apt-get update -qq && apt-get install -y build-essential libpq-dev nodejs

RUN mkdir /rails_nginx_docker
WORKDIR /rails_nginx_docker

ADD Gemfile /rails_nginx_docker/Gemfile
ADD Gemfile.lock /rails_nginx_docker/Gemfile.lock

RUN gem uninstall bundler -a \
      && gem install bundler -v 2.0.1 \
      && bundle install

ADD . /rails_nginx_docker
EXPOSE 3000
CMD [ "bundle", "exec", "puma", "-C", "config/puma.rb" ]