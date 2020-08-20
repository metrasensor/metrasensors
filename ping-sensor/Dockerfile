FROM  telegraf:1.15-alpine

ARG   EMPTY
ENV   PROJECT_UUID=$EMPTY
ENV   SENSOR_NAME=ping
ENV   RECEIVER_HOST=udp://receiver.metrasensor.com

COPY  telegraf.conf /etc/telegraf/

CMD   ["telegraf"]