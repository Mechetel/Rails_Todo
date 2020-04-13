# Ruby Base image:
FROM ruby:2.6.3
# Install dependencies 
RUN apt-get update -qq && apt-get install -y build-essential libpq-dev nodejs
# create application directory
RUN mkdir /Rails_Todo
# Set our working directory inside the image
WORKDIR /Rails_Todo
ADD Gemfile /Rails_Todo/Gemfile
ADD Gemfile.lock /Rails_Todo/Gemfile.lock
RUN bundle install
ADD . /Rails_Todo
EXPOSE 3000
CMD [ "bundle", "exec", "puma", "-C", "config/puma.rb" ]