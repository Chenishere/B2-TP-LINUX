FROM debian
RUN apt update -y
RUN apt install -y apache2
COPY apache2.conf /etc/apache2/apache2.conf
COPY index.html /var/www/html/index.html
EXPOSE 80/tcp
RUN mkdir /etc/apache2/logs
CMD [ "apache2", "-DFOREGROUND" ]
