FROM debian:jessie

MAINTAINER Maxence POUTORD <maxence.poutord@gmail.com>

RUN apt-get update && apt-get install -y \
    nginx

ADD nginx.conf /etc/nginx/
ADD symfony.conf /etc/nginx/sites-available/
ADD wbi-user.conf /etc/nginx/sites-available/
ADD me.conf /etc/nginx/sites-available/

RUN ln -s /etc/nginx/sites-available/symfony.conf /etc/nginx/sites-enabled/symfony
RUN ln -s /etc/nginx/sites-available/wbi-user.conf /etc/nginx/sites-enabled/wbi-user
RUN ln -s /etc/nginx/sites-available/me.conf /etc/nginx/sites-enabled/me
RUN rm /etc/nginx/sites-enabled/default

## add majdi-user.dev in hosts with nginx

RUN echo "upstream php-upstream { server php:9000; }" > /etc/nginx/conf.d/upstream.conf

RUN usermod -u 1000 www-data

CMD ["nginx"]

EXPOSE 80
EXPOSE 443
