FROM ubuntu:trusty
MAINTAINER Zenoss, Inc. <dev@zenoss.com>

ENV DEBIAN_FRONTEND noninteractive
RUN BUILD_DEPS="build-essential libfuse-dev libcurl4-openssl-dev libxml2-dev mime-support automake libtool wget tar";  \
    set -x; \
    apt-get update -qq && \
    apt-get install -y $BUILD_DEPS --no-install-recommends && \
    set -x; \
    rm -rf /var/lib/apt/lists/* && \
    wget --no-check-certificate -qO /tmp/s3fs-1.74.tar.gz https://s3fs.googlecode.com/files/s3fs-1.74.tar.gz  && \
    tar -C /tmp -xzf /tmp/s3fs-1.74.tar.gz && \
    cd /tmp/s3fs-1.74 && \
    ./configure --prefix=/usr/local && \
    make && \
    make install && \
    set -x; \
    rm -rf /tmp/s3fs-1.7.4* && \
    apt-get remove --purge -y build-essential libfuse-dev libcurl4-openssl-dev libxml2-dev mime-support automake libtool wget tar && \
    apt-get autoremove -y
