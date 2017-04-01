#!/bin/sh
. /etc/sysconfig/docker
[ -e "${DOCKER_CONTAINERD_BINARY}" ] || DOCKER_CONTAINERD_BINARY=/usr/bin/docker-containerd-current
if [ ! -f /usr/bin/docker-containerd-current ]; then
    DOCKER_CONTAINERD_BINARY=/usr/bin/docker-containerd-latest
fi
if [[ ${DOCKER_CONTAINERD_BINARY} != "/usr/bin/docker-containerd-current" && ${DOCKER_CONTAINERD_BINARY} != /usr/bin/docker-containerd-latest ]]; then
    echo "DOCKER_CONTAINERD_BINARY has been set to an invalid value:" $DOCKER_CONTAINERD_BINARY
    echo ""
    echo "Please set DOCKER_CONTAINERD_BINARY to /usr/bin/docker-containerd-current or /usr/bin/docker-containerd-latest
by editing /etc/sysconfig/docker"
else
    exec ${DOCKER_CONTAINERD_BINARY} "$@"
fi
