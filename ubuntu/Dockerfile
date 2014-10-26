FROM ubuntu:trusty
MAINTAINER Zenoss, Inc. <dev@zenoss.com>

ENV DEBIAN_FRONTEND noninteractive
RUN BUILD_DEPS="build-essential automake libtool";  \
    set -x; \
    apt-get update && \
    apt-get install -y wget tar libfuse-dev libcurl4-openssl-dev libxml2-dev mime-support $BUILD_DEPS && \
    rm -rf /var/lib/apt/lists/* && \
    wget --no-check-certificate -qO /tmp/s3fs-1.74.tar.gz https://s3fs.googlecode.com/files/s3fs-1.74.tar.gz  && \
    tar -C /tmp -xzf /tmp/s3fs-1.74.tar.gz && \
    cd /tmp/s3fs-1.74 && \
    ./configure --prefix=/usr/local && \
    make && \
    make install && \
    rm -rf /tmp/s3fs-1.7.4* && \
    apt-get -y -f install && \
    apt-get purge -y $BUILD_DEPS && \
    apt-get autoremove -y
