FROM ruby

RUN apt-get update && apt-get -y dist-upgrade
RUN apt-get install git
RUN gem install rails bundler

ONBUILD RUN git clone https://github.com/IBM-Cloud/ruby-rails-helloworld.git /opt/app
ONBUILD RUN cd /opt/app && bundle install

ENTRYPOINT /bin/sh


## Son
#FROM ft-rails:on-build

#EXPOSE 3000

#CMD ["rails", "s", "-b", "0.0.0.0", "-p" ,"3000"]

#docker build -t ft-rails:on-build .
#docker run -it --rm --name rails ft-rails:on-build