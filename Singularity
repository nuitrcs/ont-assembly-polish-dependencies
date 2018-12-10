Bootstrap: docker
From: ubuntu:16.04

%post
    apt-get update && apt-get upgrade -y && apt-get install -y \
        sudo git make build-essential mummer last-align python-numpy \
        python-matplotlib time bwa samtools software-properties-common \
        gnuplot zlib1g-dev mc wget libatlas-base-dev python-pip python-pandas
    add-apt-repository ppa:webupd8team/java && apt-get update && \
        (echo "oracle-java8-installer shared/accepted-oracle-license-v1-1 select true" | sudo debconf-set-selections) && \
        apt-get install -y oracle-java8-installer
    cd /opt
    git clone https://github.com/marbl/canu.git && cd canu/src && make -j && cd -
    git clone https://github.com/lh3/minimap2 && (cd minimap2 && make) && \
        cp minimap2/minimap2 /usr/local/bin && rm -r minimap2
    git clone https://github.com/lh3/miniasm && (cd miniasm && make) && \
        cp miniasm/miniasm /usr/local/bin/ && rm -r miniasm
    git clone https://github.com/timmassingham/simNGS.git && (cd simNGS/src && make -f Makefile.linux) && \
        cp simNGS/bin/* /usr/local/bin/ && rm -r simNGS

%environment
    PATH=/opt/canu/Linux-amd64/bin:$PATH
    export PATH

%runscript
    exec /bin/bash -i