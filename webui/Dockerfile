# Dockerfile for building NetXMS webui

FROM tomcat:9
LABEL maintainer = "Ivan Bondarev <bondarev.ia@sentium.ru>"

ENV VERSION=3.9.156 NETXMS_SERVER=netxms-server NETXMS_SESSIONTIMEOUT=-1 NETXMS_ENABLEADVANCEDSETTINGS=true

COPY ./docker-entrypoint.sh /

RUN echo 'debconf debconf/frontend select Noninteractive' | debconf-set-selections && \
    apt-get update && apt-get -y install curl apt-transport-https && \
    curl -L https://netxms.org/download/releases/3.9/nxmc-${VERSION}.war -o /usr/local/tomcat/webapps/nxmc.war && \
    chmod 755 /docker-entrypoint.sh

ENTRYPOINT [ "/docker-entrypoint.sh" ]
