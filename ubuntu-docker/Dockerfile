# docker base image for ansible network automation

FROM ubuntu:focal

RUN DEBIAN_FRONTEND=noninteractive apt-get update && apt-get -y --no-install-recommends \
    install apt-utils telnet net-tools traceroute openssh-client nano vim-tiny \
    iputils-ping software-properties-common \
    && apt-add-repository -y ppa:ansible/ansible-2.9 \
    && apt-get update && apt-get -y --no-install-recommends install ansible \
    && apt-get autoremove \
    && apt-get autoclean \
    && rm -rf /var/lib/apt/lists/* \
    && mkdir /root/.ssh/ \
    && echo "KexAlgorithms diffie-hellman-group1-sha1,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384 ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group14-sha1" > /root/.ssh/config \
    && echo "Ciphers 3des-cbc,blowfish-cbc,aes128-cbc,aes128-ctr,aes256-ctr" >> /root/.ssh/config \
    && chown root /root/.ssh/    

VOLUME [ "/root" ]
CMD [ "sh", "-c", "cd; exec bash -i" ]