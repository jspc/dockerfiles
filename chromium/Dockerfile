# chromium
#
#
# Build: docker build -t chromium .
#
# Run: docker run --hostname=chromium -ti --shm-size=2g \
#                 -e DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix:rw  \
#                 -v ${DATA_MOUNT}/chromium:/data:rw  -v ${DATA_MOUNT}/usrdata/downloads:/home/user/Downloads:rw chromium
#
# Note: ${DATA_MOUNT}/chromium/data is the mount point of the associated USB drive. By not mounting this, session state will be ephemeral.
#       Pointing to `usrdata/Downloads` will allow for persistent downloads and files and stuff.
#
#       Also: this will almost certainly require the command: `xhost +local:chromium` to give chromium access to the xserver

FROM alpine:edge
MAINTAINER jspc <james@zero-internet.org.uk>

RUN apk add --update --no-cache chromium dbus-dev udev ttf-dejavu && \
    rm -rf /var/cache/apk && \
    adduser -h /home/user -s /bin/false -S -D -u 1000 chromium

USER chromium

ENTRYPOINT [ "/usr/lib/chromium/chrome" ]
CMD [ "--no-sandbox", "--user-data-dir=/data", "--disable-gpu" ]
