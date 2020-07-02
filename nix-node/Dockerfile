FROM  telegraf:1.14.4-alpine

ARG   EMPTY
ENV   PROJECT_UUID=$EMPTY
ENV   RECEIVER_HOST=udp://receiver.metrasensor.com
ENV   PROMETHEUS_HOST=http://localhost:9100/metrics

COPY  telegraf.conf /etc/telegraf/

CMD   ["telegraf"]