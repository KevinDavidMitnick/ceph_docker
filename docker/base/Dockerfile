FROM centos:latest
MAINTAINER Kolla Project (https://launchpad.net/kolla)
LABEL kolla_version="2.0.3"
ENV KOLLA_BASE_DISTRO centos
ENV KOLLA_INSTALL_TYPE binary
ENV KOLLA_INSTALL_METATYPE rdo

#### Customize PS1 to be used with bash shell
COPY kolla_bashrc /tmp/
RUN cat /tmp/kolla_bashrc >> /etc/skel/.bashrc
RUN cat /tmp/kolla_bashrc >> /root/.bashrc

# PS1 var when used /bin/sh shell
ENV PS1="$(tput bold)($(printenv KOLLA_SERVICE_NAME))$(tput sgr0)[$(id -un)@$(hostname -s) $(pwd)]$ "


# Pin package versions
RUN rm -rf /etc/yum.repos.d/*

COPY CentOS-Base.repo /etc/yum.repos.d/
COPY epel.repo /etc/yum.repos.d/
COPY ceph.repo /etc/yum.repos.d/

RUN yum clean all && yum makecache
    
# Install base packages
RUN yum install -y \
        sudo \
        which \
        python \
    && yum clean all

    
COPY set_configs.py /usr/local/bin/kolla_set_configs
COPY start.sh /usr/local/bin/kolla_start
COPY sudoers /etc/sudoers
RUN touch /usr/local/bin/kolla_extend_start \
    && chmod 755 /usr/local/bin/kolla_start /usr/local/bin/kolla_extend_start /usr/local/bin/kolla_set_configs \
    && chmod 440 /etc/sudoers \
    && groupadd kolla

RUN rm -f /tmp/kolla_bashrc 

COPY dumb-init_1.1.3_amd64 /usr/local/bin/dumb-init

RUN chmod +x /usr/local/bin/dumb-init

CMD ["kolla_start"]
