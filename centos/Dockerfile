FROM docker.io/centos:7.5.1804

USER root

RUN yum -y groupinstall "Development Tools" \
 && yum -y install expat-devel

CMD ["/bin/bash"]