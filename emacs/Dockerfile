# emacs
#
#
# Build: docker build -t emacs .
#
# Run:
#   X11:
#       docker run --hostname=emacs -ti\
#                 -e DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix:rw  \
#                 -v ${DATA_MOUNT}/usrdata:/home/user:rw emacs
#   Console:
#       docker run --hostname=emacs -ti\
#                 -v ${DATA_MOUNT}/usrdata:/home/user:rw emacs
#
# Note: ${DATA_MOUNT}is the mount point of the associated USB drive
#
#       We expose(?) the volume containing our emacs server. This allows for other
#       containers to connect to the server

FROM alpine:edge
MAINTAINER jspc <james@zero-internet.org.uk>

RUN apk add --update --no-cache emacs-x11 ttf-dejavu && \
    rm -rf /var/cache/apk && \
    adduser -h /home/user -s /bin/false -S -D -u 1000 emacs

RUN install -d -m 0700 -o emacs /tmp/emacs1000
VOLUME /tmp/emacs1000

USER emacs

ENTRYPOINT ["/usr/bin/emacs"]
