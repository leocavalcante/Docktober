FROM httpd:2.4

COPY ./httpd.conf /usr/local/apache2/conf/httpd.conf

RUN apt-get update && apt-get install -y \
    libapache2-mod-proxy-html \
    libxml2-dev

RUN apachectl -k restart
