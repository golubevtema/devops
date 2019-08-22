FROM ubuntu:latest

RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone && \
    apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get -y upgrade && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y curl sudo && \
    useradd --no-create-home --shell /bin/false node_exporter && \
    cd /tmp && \
    curl -LO https://github.com/prometheus/node_exporter/releases/download/v0.18.1/node_exporter-0.18.1.linux-amd64.tar.gz && \
    tar xzvf node_exporter-0.18.1.linux-amd64.tar.gz && \
    cp node_exporter-0.18.1.linux-amd64/node_exporter /usr/local/bin && \
    chown node_exporter:node_exporter /usr/local/bin/node_exporter

EXPOSE 9100

CMD ["/usr/local/bin/node_exporter"]

