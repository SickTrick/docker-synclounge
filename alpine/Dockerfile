FROM node:lts-alpine

ENV DOMAIN=watch.1222.tech
ENV webroot=
ENV serverroot=/slserver
ENV autoJoin=true
ENV autoJoinServer=server.1222.tech/slserver
ENV autoJoinRoom=
ENV autoJoinPassword=
ENV plexToken=

COPY run.sh /opt/run.sh

RUN apk add --no-cache git make g++ python bash \
  && mkdir -p /opt && cd /opt \
  && git clone https://github.com/SickTrick/synclounge \
  && cd synclounge \
  && npm install \
  && npm run build \
  && apk del make g++ python \
  && rm -rf /tmp/* /root/* \
  && chmod a+x /opt/run.sh


EXPOSE 8088

CMD ["/opt/run.sh"]
