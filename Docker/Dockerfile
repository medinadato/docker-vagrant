# Ubuntu

FROM ubuntu:15.04

MAINTAINER Renato Medina, medina@mdnsolutions.com

# Download and install php, nginx, and supervisor, hey, just linux for a change!
RUN apt-get update
RUN apt-get install -y software-properties-common
RUN add-apt-repository ppa:nginx/stable
RUN apt-get update
RUN apt-get -y dist-upgrade
RUN apt-get install -y php5-fpm nginx supervisor

# Setup config files
RUN echo "daemon off;" >> /etc/nginx/nginx.conf
#ADD ./nginx/default /etc/nginx/sites-enabled/default
ADD ./supervisor/supervisord.conf /etc/supervisor/supervisord.conf
ADD ./php-fpm/php-fpm.conf /etc/php5/fpm/php-fpm.conf

# Shared volume
RUN mkdir -p /var/www
VOLUME ["/var/www"]

# Default command for container, start supervisor
CMD ["supervisord", "--nodaemon"]
USER root

# Expose port 80 of the container
EXPOSE 80
