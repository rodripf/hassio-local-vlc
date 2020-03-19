#ARG BUILD_FROM
ARG BUILD_FROM=hassioaddons/base:7.0.3
FROM $BUILD_FROM

ENV LANG C.UTF-8

# Copy data for add-on
ENV HOME=/home/vlc
RUN apk update
RUN apk add --no-cache alsa-plugins-pulse
RUN apk add --no-cache vlc
RUN sed -i 's/geteuid/getppid/' /usr/bin/vlc
RUN sed -i '197s#.*#    dir = dir == undefined ? "file:///share" : dir;#' /usr/share/vlc/lua/http/js/controllers.js
COPY run.sh /
RUN chmod a+x /run.sh

ENTRYPOINT [ "/run.sh" ]
