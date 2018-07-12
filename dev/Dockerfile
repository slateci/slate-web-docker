FROM centos:centos7
LABEL maintainer lincolnb@uchicago.edu
LABEL version 2018.7.12-1

RUN yum install epel-release -y 
RUN yum install git python-pip nginx python-devel supervisor pip uwsgi uwsgi-plugin-python -y 
RUN yum groupinstall "Development Tools" -y

RUN mkdir -p /srv/www
RUN git clone https://github.com/slateci/prototype-portal /srv/www/slate-web
RUN cd /srv/www/slate-web; pip install -r requirements.txt

# Config files
COPY uwsgi_params /etc/nginx/uwsgi_params
COPY nginx.conf /etc/nginx/nginx.conf
COPY supervisord.conf /etc/supervisord.conf

CMD ["/usr/bin/supervisord","-c","/etc/supervisord.conf"]
