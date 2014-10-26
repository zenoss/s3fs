FROM centos:centos7
MAINTAINER Zenoss, Inc <dev@zenoss.com>

RUN BUILD_DEPS="wget gcc make tar libstdc++-devel gcc-c++ curl-devel libxml2-devel openssl-devel mailcap fuse-devel"; \
    set -x; \
    yum update -y && \
    yum install -y $BUILD_DEPS && \
    wget -qO /tmp/s3fs-1.74.tar.gz https://s3fs.googlecode.com/files/s3fs-1.74.tar.gz && \
    tar -C /tmp -xzf /tmp/s3fs-1.74.tar.gz && \
    cd /tmp/s3fs-1.74 && \
    ./configure --prefix=/usr/local && \
    make && \
    make install && \
    rm -rf /tmp/s3fs-1.74* && \
    yum erase -y $BUILD_DEPS && \
    yum clean all

CMD ["/bin/bash"]
