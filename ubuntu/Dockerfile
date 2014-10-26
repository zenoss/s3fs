FROM ubuntu:trusty
MAINTAINER Zenoss, Inc. <dev@zenoss.com>

ENV DEBIAN_FRONTEND noninteractive
RUN BUILD_DEPS="build-essential libfuse-dev libcurl4-openssl-dev libxml2-dev mime-support automake libtool curl tar";  \
    set -x; \
    apt-get update -qq && \
    apt-get install -y $BUILD_DEPS --no-install-recommends && \
    rm -rf /var/lib/apt/lists/* && \
    wget -qO /tmp/s3fs-1.74.tar.gz https://s3fs.googlecode.com/files/s3fs-1.74.tar.gz  && \
    tar -C /tmp -xzf /tmp/s3fs-1.74.tar.gz && \
    cd /tmp/s3fs-1.74 && \
    ./autogen.sh && \
    ./configure --prefix=/usr && \
    make && \
    make install && \
    rm -rf /tmp/s3fs-1.7.4* && \
    apt-get purge -y $BUILD_DEPS && \
    apt-get autoremove -y
