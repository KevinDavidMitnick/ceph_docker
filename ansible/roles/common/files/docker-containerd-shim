#!/bin/sh
. /etc/sysconfig/docker
[ -e "${DOCKER_CONTAINERD_SHIM_BINARY}" ] || DOCKER_CONTAINERD_SHIM_BINARY=/usr/bin/docker-containerd-shim-current
if [ ! -f /usr/bin/docker-containerd-shim-current ]; then
    DOCKER_CONTAINERD_SHIM_BINARY=/usr/bin/docker-containerd-shim-latest
fi
if [[ ${DOCKER_CONTAINERD_SHIM_BINARY} != "/usr/bin/docker-containerd-shim-current" && ${DOCKER_CONTAINERD_SHIM_BINARY} != /usr/bin/docker-containerd-shim-latest ]]; then
    echo "DOCKER_CONTAINERD_SHIM_BINARY has been set to an invalid value:" $DOCKER_CONTAINERD_SHIM_BINARY
    echo ""
    echo "Please set DOCKER_CONTAINERD_SHIM_BINARY to /usr/bin/docker-containerd-shim-current or /usr/bin/docker-containerd-shim-latest
by editing /etc/sysconfig/docker"
else
    exec ${DOCKER_CONTAINERD_SHIM_BINARY} "$@"
fi
