FROM  telegraf:1.14.2-alpine

ARG   EMPTY
ENV   ADDRESS=$EMPTY
ENV   PROJECT_UUID=$EMPTY
COPY  telegraf.conf /etc/telegraf/

CMD   ["telegraf"]