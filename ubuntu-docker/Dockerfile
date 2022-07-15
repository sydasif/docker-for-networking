# docker base image for ansible network automation

FROM ubuntu:focal

RUN DEBIAN_FRONTEND=noninteractive apt-get update && apt-get -y --no-install-recommends \
    install apt-utils telnet net-tools openssh-client nano python3-pip \
    iputils-ping software-properties-common \
    && apt-add-repository -y ppa:ansible/ansible-2.9 \
    && apt-get update && apt-get -y --no-install-recommends install ansible \
    && apt-get autoremove \
    && apt-get autoclean \
    && pip install paramiko wheel \
    && rm -rf /var/lib/apt/lists/*

VOLUME [ "/root" ]
CMD [ "sh", "-c", "cd; exec bash -i" ]