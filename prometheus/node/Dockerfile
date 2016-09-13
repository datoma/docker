FROM alpine:3.2
MAINTAINER Michael Hoffmann
RUN apk update && \
    apk add bash && \
    rm /var/cache/apk/*
ADD https://github.com/prometheus/node_exporter/releases/download/0.12.0/node_exporter-0.12.0.linux-amd64.tar.gz /tmp/
WORKDIR /tmp
RUN tar -xzf node_exporter-0.12.0.linux-amd64.tar.gz && \
    mv node_exporter-0.12.0.linux-amd64/node_exporter /usr/local/bin/ && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

EXPOSE 9100

ENTRYPOINT [ "/usr/local/bin/node_exporter" ]
