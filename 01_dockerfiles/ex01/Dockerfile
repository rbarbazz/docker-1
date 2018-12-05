FROM debian

RUN apt-get -qq update && apt-get -qq install -y wget bzip2

RUN wget -q https://files.teamspeak-services.com/releases/server/3.5.0/teamspeak3-server_linux_amd64-3.5.0.tar.bz2

RUN tar -xjf teamspeak3-server_linux_amd64-3.5.0.tar.bz2

#RUN cd teamspeak3-server_linux_amd64 && chmod 777 ts3server_minimal_runscript.sh && touch .ts3server_license_accepted && ./ts3server_minimal_runscript.sh

ENTRYPOINT /bin/bash