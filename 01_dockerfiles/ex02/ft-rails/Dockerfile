FROM ruby

RUN apt-get update && apt-get -y dist-upgrade
RUN apt-get install -y nodejs
RUN gem install rails bundler

ONBUILD COPY blog /opt/app
ONBUILD WORKDIR /opt/app

ONBUILD RUN bundle install
ONBUILD RUN rails db:migrate
ONBUILD RUN rails db:seed