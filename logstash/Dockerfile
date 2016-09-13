FROM debian:jessie
MAINTAINER Michael Hoffmann

#RUN apt-get update && apt-get -y upgrade && apt-get clean
ENV DEBIAN_FRONTEND noninteractive 
RUN apt-get update && \
    apt-get install -y \
      apt-utils \
      ca-certificates \
      bash \
      bash-completion \
      ncurses-base \
      vim \
      gettext \
      curl \
      wget \
      logrotate \
      supervisor \
      less \
      git \
      subversion \
      default-jdk \
      apt-transport-https \
      procps && \
    apt-get clean && \
    mkdir -p /etc/logrotate.docker.d && \
    wget -qO - https://packages.elastic.co/GPG-KEY-elasticsearch | apt-key add -&& \
    echo "deb https://packages.elastic.co/logstash/2.4/debian stable main" | tee -a /etc/apt/sources.list && \
    apt-get update && \
    apt-get install logstash && \
    apt-get clean

COPY supervisor/supervisord.conf /etc/supervisor/
COPY supervisor/logstash.conf /etc/supervisor/conf.d/
COPY logstash/simple.conf /etc/logstash/conf.d/
# sample Logfile to parse
COPY logstash/sampleDataSet.log /var/log/logstash/

ENV TERM xterm
#CMD ["bash"]
CMD ["/usr/bin/supervisord", "-n"]
