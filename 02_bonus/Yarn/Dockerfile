FROM ubuntu

WORKDIR /app

RUN apt-get update && apt-get install -y curl gnupg
RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add -
RUN echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list
RUN curl -sL https://deb.nodesource.com/setup_11.x | bash -
RUN apt-get update && apt-get install -y nodejs yarn

COPY . /app

RUN yarn install

#Commands to use from the app's directory

#docker build -t yarni .
#docker run -ti yarni