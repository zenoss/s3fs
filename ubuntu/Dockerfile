FROM ubuntu:trusty
MAINTAINER Zenoss, Inc. <dev@zenoss.com>

ENV DEBIAN_FRONTEND noninteractive
RUN BUILD_DEPS="build-essential libfuse-dev libcurl4-openssl-dev libxml2-dev mime-support automake libtool wget tar";  \
    set -x; \
    apt-get update -qq && \
    apt-get install -y $BUILD_DEPS --no-install-recommends && \
    rm -rf /var/lib/apt/lists/* && \
    wget -qO- https://github.com/s3fs-fuse/s3fs-fuse/archive/v1.78.tar.gz | tar cz -C /tmp && \
    cd /tmp/s3fs-fuse-1.78 && \
    ./autogen.sh && \
    ./configure --prefix=/usr && \
    make && \
    make install && \
    rm -rf /usr/src && \
    apt-get purge -y $BUILD_DEPS && \
    apt-get autoremove -y
