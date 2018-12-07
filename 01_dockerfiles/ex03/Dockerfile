FROM debian

RUN apt-get update && apt-get install -y curl openssh-server ca-certificates postfix
RUN curl -O https://packages.gitlab.com/install/repositories/gitlab/gitlab-ee/script.deb.sh
RUN bash script.deb.sh
RUN EXTERNAL_URL="http://gitlab.example.com" apt-get install gitlab-ee


#docker build -t gitlabi .