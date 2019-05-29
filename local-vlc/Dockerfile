#ARG BUILD_FROM
ARG BUILD_FROM=hassioaddons/base:3.1.1
FROM $BUILD_FROM

ENV LANG C.UTF-8

# Copy data for add-on
ENV HOME=/home/vlc
RUN apk update
RUN apk add --no-cache vlc
RUN sed -i 's/geteuid/getppid/' /usr/bin/vlc
COPY run.sh /
RUN chmod a+x /run.sh

ENTRYPOINT [ "/run.sh" ]
