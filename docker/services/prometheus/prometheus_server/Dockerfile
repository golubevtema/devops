FROM ubuntu:latest

COPY prometheus_run.sh /usr/local/bin/

RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone && \
    apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get -y upgrade && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y curl && \
    useradd -s /bin/bash -d /home/prometheus -m prometheus && \
    mkdir -p /etc/prometheus && \
    mkdir -p /var/lib/prometheus && \
    cd /tmp && \
    curl -LO https://github.com/prometheus/prometheus/releases/download/v2.12.0/prometheus-2.12.0.linux-amd64.tar.gz && \
    tar xzvf prometheus-2.12.0.linux-amd64.tar.gz && \
    cp prometheus-2.12.0.linux-amd64/prometheus /usr/local/bin/ && \
    cp prometheus-2.12.0.linux-amd64/promtool /usr/local/bin/ && \
    cp -r prometheus-2.12.0.linux-amd64/consoles /etc/prometheus/ && \
    cp -r prometheus-2.12.0.linux-amd64/console_libraries /etc/prometheus/ && \
    chown -R prometheus:prometheus /etc/prometheus && \
    chown -R prometheus:prometheus /var/lib/prometheus && \
    chmod +x /usr/local/bin/prometheus_run.sh

COPY prometheus.yml /etc/prometheus/

EXPOSE 9090

USER prometheus

CMD ["/usr/local/bin/prometheus_run.sh"]

