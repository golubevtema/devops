FROM ubuntu:latest

RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone && \
    apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get -y upgrade && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y curl && \
    useradd -s /bin/bash -d /opt/grafana -m grafana && \
    cd /tmp && \
    curl -LO https://dl.grafana.com/oss/release/grafana-6.3.3.linux-amd64.tar.gz && \
    tar xzvf grafana-6.3.3.linux-amd64.tar.gz && \
    cp -r grafana-6.3.3/* /opt/grafana && \
    chown -R grafana:grafana /opt/grafana

USER grafana

WORKDIR /opt/grafana

EXPOSE 3000

CMD ["/opt/grafana/bin/grafana-server"]

