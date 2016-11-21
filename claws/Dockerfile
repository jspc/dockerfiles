# claws
#
#
# Build: docker build -t claws .
#
# Run: docker run --hostname=claws -ti \
#                 -e DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix:rw  \
#                 -v ${DATA_MOUNT}/claws:/home/user/.claws-mail:rw claws
#
# Note: ${DATA_MOUNT}/claws is the mount point of the associated USB drive. By not mounting this, session state will be ephemeral.
#       Pointing to `usrdata/Downloads` will allow for persistent downloads and files and stuff.
#
#       Also: this will almost certainly require the command: `xhost +local:claws` to give claws access to the xserver

FROM alpine:edge
MAINTAINER jspc <james@zero-internet.org.uk>

RUN apk add --update --no-cache ca-certificates ttf-dejavu claws-mail claws-mail-plugins-pgp && \
    rm -rf /var/cache/apk && \
    adduser -h /home/user -s /bin/false -S -D -u 1000 claws

USER claws

ENTRYPOINT [ "/usr/bin/claws-mail" ]
