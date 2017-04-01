# ceph_docker
i cut ceph  related code from kolla-ansible project,when you build ceph from docker,you can deploy this by ansible.
this is not finished,i will add host ansible deploy code later.
depency:
    centos:7.3.1611
    ansible:1.9.6
    docker:1.3
    docker-py:latest
exec:ansible-playbook -i inventory/hosts -e  action=deploy site.yml

ceph osd prefix must be:KOLLA_CEPH_OSD_BOOTSTRAP to be found

