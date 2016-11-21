# shell
#
#
# Build: docker build -t shell .
#
# Run: docker run --hostname=shell -ti \
#                 --volumes-from=emacs \
#                 -v ${DATA_MOUNT}/usrdata:/home/user:rw shell
#
# Note: ${DATA_MOUNT}/shell is the mount point of the associated USB drive. By not mounting this, session state will be ephemeral.
#       Pointing to `usrdata/Downloads` will allow for persistent downloads and files and stuff.
#
#       Using '--volumes-from=emacs' will, so long as the emacs container is running, allow for client/server communications

FROM alpine:edge
MAINTAINER jspc <james@zero-internet.org.uk>

RUN apk add --update --no-cache ca-certificates alpine-sdk emacs bash bash-completion git-bash-completion curl go openssh && \
    rm -rf /var/cache/apk && \
    adduser -h /home/user -s /bin/false -S -D -u 1000 jspc

USER jspc
WORKDIR /home/user

ENTRYPOINT [ "/bin/bash" ]
