FROM debian

ENV VMURL=192.168.99.100
RUN apt-get update && apt-get install -y curl openssh-server ca-certificates postfix
RUN curl -O https://packages.gitlab.com/install/repositories/gitlab/gitlab-ee/script.deb.sh
RUN bash script.deb.sh
RUN EXTERNAL_URL= apt-get install gitlab-ee
RUN echo "gitlab_rails['gitlab_shell_ssh_port'] = 42022" >> /etc/gitlab/gitlab.rb
RUN echo "external_url \"https://$VMURL\"" >> /etc/gitlab/gitlab.rb
RUN echo #!/bin/sh > /docker-entrypoint.sh
RUN echo "mkdir -p /etc/gitlab/ssl" >> /docker-entrypoint.sh
RUN echo "chmod 700 /etc/gitlab/ssl" >> /docker-entrypoint.sh
RUN echo "openssl req -newkey rsa:2048 -nodes -keyout $VMURL.key -x509 -subj \"/C=US/ST=Denial/L=Springfield/O=Dis/CN=www.example.com\" -days 365 -out $VMURL.crt" >> /docker-entrypoint.sh
RUN echo "cp $VMURL.key $VMURL.crt /etc/gitlab/ssl/" >> /docker-entrypoint.sh
RUN echo "service ssh start" >> /docker-entrypoint.sh
RUN echo "/opt/gitlab/embedded/bin/runsvdir-start &" >> /docker-entrypoint.sh
RUN echo "gitlab-ctl reconfigure" >> /docker-entrypoint.sh
RUN chmod 777 /docker-entrypoint.sh

EXPOSE 80
EXPOSE 22
EXPOSE 443

#docker-machine stop Char
#VBoxManage modifyvm Char --cpus 2
#VBoxManage modifyvm Char --memory 4096
#docker-machine start Char
#docker build -t gitlabi .
#docker run -ti --privileged --name fox -p 80:80 -p 42022:22 -p 443:443 gitlabi
#git config --global http.sslVerify false