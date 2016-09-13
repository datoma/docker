FROM alpine:3.2
ENV GOPATH=/gocode
RUN apk --update add go go-tools g++ godep git nodejs && mkdir /etc/grafana && mkdir /gocode
RUN go get -v github.com/grafana/grafana
WORKDIR /gocode/src/github.com/grafana/grafana
RUN go build -v .
RUN npm install && npm install -g grunt-cli && grunt
ADD defaults.ini /etc/grafana/defaults.ini
EXPOSE 3000
CMD ["./grafana", "-config=/etc/grafana/defaults.ini"]



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




FROM

export HTTP_PROXY=http://myproxy.com:8080

