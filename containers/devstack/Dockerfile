FROM ubuntu:14.04.3
MAINTAINER XOS Project http://xosproject.org

RUN apt-get update -y && \
    apt-get install -y git

RUN git clone https://git.openstack.org/openstack-dev/devstack /usr/local/src/devstack && \
    cp /usr/local/src/devstack/samples/local.conf /usr/local/src/devstack/local.conf && \
    cp /usr/local/src/devstack/samples/local.sh /usr/local/src/devstack/local.sh && \
    /usr/local/src/devstack/tools/create-stack-user.sh && \
    chown -R stack.stack /usr/local/src/devstack

USER stack

WORKDIR /usr/local/src/devstack

#RUN ./stack.sh
