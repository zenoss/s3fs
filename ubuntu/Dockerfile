FROM ubuntu:trusty
MAINTAINER Zenoss, Inc. <dev@zenoss.com>

ENV DEBIAN_FRONTEND noninteractive
RUN BUILD_DEPS="build-essential libfuse-dev libcurl4-openssl-dev libxml2-dev mime-support automake libtool wget tar";  \
    set -x; \
    apt-get update -qq && \
    apt-get install -y $BUILD_DEPS --no-install-recommends && \
    rm -rf /var/lib/apt/lists/* && \
    wget -qO /tmp/v1.74.tar.gz https://s3fs.googlecode.com/files/s3fs-1.74.tar.gz && \
    tar -C /tmp -xzf /tmp/v1.74.tar.gz && \
    rm -f /tmp/v1.74.tar.gz && \
    cd /tmp/s3fs-fuse-1.74 && \
    ./autogen.sh && \
    ./configure --prefix=/usr && \
    make && \
    make install && \
    rm -rf /usr/src && \
    apt-get purge -y $BUILD_DEPS && \
    apt-get autoremove -y
