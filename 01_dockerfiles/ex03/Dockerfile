FROM debian

ENV VMURL=192.168.99.100
RUN apt-get update && apt-get install -y curl openssh-server ca-certificates postfix \
	&& curl -O https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh \
	&& bash script.deb.sh \
	&& EXTERNAL_URL= apt-get install gitlab-ce
RUN echo "gitlab_rails['gitlab_shell_ssh_port'] = 42022" >> /etc/gitlab/gitlab.rb \
	&& echo "external_url \"https://$VMURL\"" >> /etc/gitlab/gitlab.rb
RUN echo '#!/bin/sh' > /docker-entrypoint.sh \
	&& echo "mkdir -p /etc/gitlab/ssl" >> /docker-entrypoint.sh \
	&& echo "chmod 700 /etc/gitlab/ssl" >> /docker-entrypoint.sh \
	&& echo "openssl req -newkey rsa:2048 -nodes -keyout $VMURL.key -x509 -subj \"/C=US/ST=Denial/L=Springfield/O=Dis/CN=www.example.com\" -days 365 -out $VMURL.crt" >> /docker-entrypoint.sh \
	&& echo "cp $VMURL.key $VMURL.crt /etc/gitlab/ssl/" >> /docker-entrypoint.sh \
	&& echo "service ssh start" >> /docker-entrypoint.sh \
	&& echo "/opt/gitlab/embedded/bin/runsvdir-start &" >> /docker-entrypoint.sh \
	&& echo "gitlab-ctl reconfigure" >> /docker-entrypoint.sh \
	&& echo "while true" >> /docker-entrypoint.sh \
	&& echo "do" >> /docker-entrypoint.sh \
	&& echo "	sleep 1" >> /docker-entrypoint.sh \
	&& echo "done" >> /docker-entrypoint.sh \
	&& chmod 777 /docker-entrypoint.sh

EXPOSE 80
EXPOSE 22
EXPOSE 443

ENTRYPOINT ["/docker-entrypoint.sh"]

#docker build -t gitlabi .
#docker run -ti --privileged -p 80:80 -p 42022:22 -p 443:443 gitlabi
#git config --global http.sslVerify false