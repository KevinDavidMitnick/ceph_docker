FROM kolla/centos-binary-base:2.0.3
MAINTAINER Kolla Project (https://launchpad.net/kolla)

RUN yum -y install \
        ceph \
        ceph-radosgw \
        parted \
        hdparm \
        btrfs-progs \
        xfsprogs \
        e2fsprogs \
    && yum clean all



COPY extend_start.sh /usr/local/bin/kolla_extend_start
RUN chmod 755 /usr/local/bin/kolla_extend_start
