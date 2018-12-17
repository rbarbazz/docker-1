ARG VMURL
FROM debian

RUN apt-get update && apt-get install -y curl openssh-server ca-certificates postfix
RUN curl -O https://packages.gitlab.com/install/repositories/gitlab/gitlab-ee/script.deb.sh
RUN bash script.deb.sh
RUN EXTERNAL_URL=$VMURL apt-get install gitlab-ee
RUN service ssh start
RUN echo "gitlab_rails['gitlab_shell_ssh_port'] = 42022" >> /etc/gitlab/gitlab.rb
RUN echo #!/bin/bash > /docker-entrypoint.sh
RUN echo "/opt/gitlab/embedded/bin/runsvdir-start &" >> /docker-entrypoint.sh
RUN echo "gitlab-ctl reconfigure" >> /docker-entrypoint.sh

EXPOSE 80
EXPOSE 22
EXPOSE 443

ENTRYPOINT ["/bin/sh", "/docker-entrypoint.sh"]

#docker-machine stop Char
#VBoxManage modifyvm Char --cpus 2
#VBoxManage modifyvm Char --memory 4096
#docker-machine start Char
#docker build --build-arg VMURL=$(docker-machine ip Char) -t gitlabi .
#docker run -it --privileged --name fox -p 80:80 -p 42022:22 -p 443:443 gitlabi