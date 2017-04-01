#!/bin/sh
. /etc/sysconfig/docker
[ -e "${DOCKERDBINARY}" ] || DOCKERDBINARY=/usr/bin/dockerd-current
if [ ! -f /usr/bin/dockerd-current ]; then
    if [ ! -f /usr/bin/dockerd-latest ]; then
        echo "You don't have either docker or \
docker-latest installed. Please install either one and retry."
        exit
    else
        DOCKERDBINARY=/usr/bin/dockerd-latest
    fi
fi
if [[ ${DOCKERDBINARY} != "/usr/bin/dockerd-current" && ${DOCKERDBINARY} != "/usr/bin/dockerd-latest" ]]; then
    echo "DOCKERDBINARY has been set to an invalid value:" $DOCKERDBINARY
    echo ""
    echo "Please set DOCKERDBINARY to /usr/bin/dockerd-current or /usr/bin/dockerd-latest
by editing /etc/sysconfig/docker"
else
    exec ${DOCKERDBINARY} "$@"
fi
