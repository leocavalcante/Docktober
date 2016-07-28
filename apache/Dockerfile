FROM httpd

RUN apt-get update && apt-get install -y \
    libapache2-mod-proxy-html \
    libxml2-dev

COPY ./httpd.conf /usr/local/apache2/conf/httpd.conf

RUN apachectl -k restart
