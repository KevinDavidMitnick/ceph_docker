#!/bin/sh
. /etc/sysconfig/docker
[ -e "${DOCKERBINARY}" ] || DOCKERBINARY=/usr/bin/docker-current
if [ ! -f /usr/bin/docker-current ]; then
    if [ ! -f /usr/bin/docker-latest ]; then
        echo "You don't have either docker-client or \
docker-client-latest installed. Please install either one and retry."
        exit
    else
        DOCKERBINARY=/usr/bin/docker-latest
    fi
fi
if [[ ${DOCKERBINARY} != "/usr/bin/docker-current" && ${DOCKERBINARY} != /usr/bin/docker-latest ]]; then
    echo "DOCKERBINARY has been set to an invalid value:" $DOCKERBINARY
    echo ""
    echo "Please set DOCKERBINARY to /usr/bin/docker-current or /usr/bin/docker-latest
by editing /etc/sysconfig/docker"
else
    exec ${DOCKERBINARY} "$@"
fi
