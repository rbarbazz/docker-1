FROM debian

RUN apt-get -qq update && apt-get -qq install -y wget bzip2
RUN wget -q https://files.teamspeak-services.com/releases/server/3.5.0/teamspeak3-server_linux_amd64-3.5.0.tar.bz2
RUN tar -xjf teamspeak3-server_linux_amd64-3.5.0.tar.bz2 && rm teamspeak3-server_linux_amd64-3.5.0.tar.bz2

ENV TS3SERVER_LICENSE=accept

EXPOSE 9987/udp
EXPOSE 10011
EXPOSE 30033

CMD ["/bin/sh", "teamspeak3-server_linux_amd64/ts3server_minimal_runscript.sh"]

#docker build -t tsi .
#docker run -it --rm -p 30033:30033 -p 10011:10011 -p 9987:9987/udp -p 41144:41144 tsi
#connect from ts on the machine's IP