FROM ubuntu:18.04

# Create user and install dependency libs
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

# Install Ascend Toolkit for x86 and arm
COPY Ascend-Toolkit-20.0.RC1-x86_64-linux_gcc7.3.0.run /home
COPY Ascend-Toolkit-20.0.RC1-arm64-linux_gcc7.3.0.run /home

RUN cd /home && \
    chmod +x *.run && \
    ./Ascend-Toolkit-*-arm64-linux_gcc*.run --check && \
    ./Ascend-Toolkit-*-x86_64-linux_gcc*.run --check && \
    ./Ascend-Toolkit-*-arm64-linux_gcc*.run --install && \
    ./Ascend-Toolkit-*-x86_64-linux_gcc*.run --install

# Install the cross-compiler
RUN apt install g++-aarch64-linux-gnu -y

# Set environment variables for ATC tool
ENV INSTALL_PATH=/usr/local/Ascend/ascend-toolkit/latest/x86_64-linux_gcc7.3.0
ENV PATH=/usr/local/python3.7.5/bin:$INSTALL_PATH/atc/ccec_compiler/bin:$INSTALL_PATH/atc/bin:$PATH
ENV PYTHONPATH=$INSTALL_PATH/atc/python/site-packages/te:$INSTALL_PATH/atc/python/site-packages/topi:$PYTHONPATH
ENV LD_LIBRARY_PATH=$INSTALL_PATH/atc/lib64:$LD_LIBRARY_PATH
ENV ASCEND_OPP_PATH=$INSTALL_PATH/opp






