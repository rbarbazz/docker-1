FROM ruby

RUN apt-get update && apt-get -y dist-upgrade
RUN apt-get install -y nodejs
RUN gem install rails bundler

ONBUILD COPY blog /opt/app
ONBUILD WORKDIR /opt/app

ONBUILD RUN bundle install
ONBUILD RUN rails db:migrate
ONBUILD RUN rails db:seed

#rails new blog
#docker build -t ft-rails:on-build ft-rails
#docker build -t son .
#docker run -it --rm --name myblog -p 3000:3000 son