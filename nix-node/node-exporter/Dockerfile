FROM        debian:stable-slim

ENV         LANG C.UTF-8
ENV         PROJECTPATH=/opt/node-exporter

ADD         . ${PROJECTPATH}
RUN         chmod +x ${PROJECTPATH}/node_exporter


WORKDIR     ${PROJECTPATH}
EXPOSE      9100
CMD         ./node_exporter

#  https://prometheus.io/docs/guides/node-exporter/ 
#  docker run --publish 9100:9100 --detach --name node-exporter node-exporter:1