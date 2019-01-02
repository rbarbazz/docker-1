FROM ubuntu

RUN apt-get update && apt-get install -y apache2

COPY . /var/www

EXPOSE 80

CMD ["apachectl", "-D", "FOREGROUND"]

#Commands to use from the app's directory

#docker build -t apachei .
#docker run -it --rm -p 80:80 apachei