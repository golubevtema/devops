FROM ubuntu:latest

RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone && \
    apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get -y upgrade && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y ca-certificates curl postfix rsync wget gem && \
    wget https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh && \
    bash script.deb.sh && \
    apt-get install -y gitlab-ce && \
    bash -c "/opt/gitlab/embedded/bin/runsvdir-start &" && \
    gitlab-ctl reconfigure && \
    gitlab-ctl stop && \
    bash -c "kill -9 $(ps aux | grep runsvdir | awk '{print $2}')"

EXPOSE 80 443

CMD ["/opt/gitlab/embedded/bin/runsvdir-start", "&"]


