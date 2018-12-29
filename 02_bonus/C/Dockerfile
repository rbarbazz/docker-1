FROM debian

WORKDIR /app

COPY . /app

RUN apt-get update && apt-get install -y clang make libncurses5-dev

RUN make

#Commands to use from the app's directory

#docker build -t clangi .
#docker run -ti clangi