FROM httpd:2.4
RUN apt-get update && apt-get install vim -y && apt-get upgrade -y
COPY conf /usr/local/apache2/conf/
COPY htdocs /usr/local/apache2/htdocs/
WORKDIR /usr/local/apache2
EXPOSE 80
CMD ["httpd-foreground"]
