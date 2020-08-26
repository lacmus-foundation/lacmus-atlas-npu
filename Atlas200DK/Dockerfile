FROM ubuntu:18.04

# Create user and install depndency libs
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

# Install Python development environment
RUN apt-get install --no-install-recommends -y wget && \
    wget https://www.python.org/ftp/python/3.7.5/Python-3.7.5.tgz && \
    tar -zxvf Python-3.7.5.tgz && \
    cd Python-3.7.5 && \
    ./configure --prefix=/usr/local/python3.7.5 --enable-shared && \
    make && \
    make install && \
    cp /usr/local/python3.7.5/lib/libpython3.7m.so.1.0 /usr/lib64 && \
    cp /usr/local/python3.7.5/lib/libpython3.7m.so.1.0 /usr/lib && \
    ln -s /usr/local/python3.7.5/bin/python3 /usr/bin/python3.7 && \
    ln -s /usr/local/python3.7.5/bin/pip3 /usr/bin/pip3.7 && \
    ln -s /usr/local/python3.7.5/bin/python3 /usr/bin/python3.7.5 && \
    ln -s /usr/local/python3.7.5/bin/pip3 /usr/bin/pip3.7.5 && \
    pip3.7.5 install attrs && \
    pip3.7.5 install psutil && \
    pip3.7.5 install decorator && \
    pip3.7.5 install numpy && \
    pip3.7.5 install protobuf==3.11.3 && \
    pip3.7.5 install scipy && \
    pip3.7.5 install sympy && \
    pip3.7.5 install cffi && \
    pip3.7.5 install grpcio && \
    pip3.7.5 install grpcio-tools && \
    pip3.7.5 install requests





