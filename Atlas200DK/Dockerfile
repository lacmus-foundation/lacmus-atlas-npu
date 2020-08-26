FROM ubuntu:18.04

RUN groupadd HwHiAiUser && \
    useradd -g HwHiAiUser -d /home/HwHiAiUser -m HwHiAiUser -p 'uloOwQBAk0/.c' && \
    apt-get update && \
    apt-get install -y gcc \
    make \
    cmake \
    zlib1g-dev \
    libsqlite3-dev \
    openssl \
    libssl-dev \
    libffi-dev \
    unzip \
    pciutils \
    net-tools
