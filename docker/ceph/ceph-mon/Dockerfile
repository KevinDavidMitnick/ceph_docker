FROM kolla/centos-binary-ceph-base:2.0.3
MAINTAINER Kolla Project (https://launchpad.net/kolla)

COPY fetch_ceph_keys.py /usr/bin/

COPY extend_start.sh /usr/local/bin/kolla_extend_start
RUN chmod 755 /usr/local/bin/kolla_extend_start /usr/bin/fetch_ceph_keys.py

