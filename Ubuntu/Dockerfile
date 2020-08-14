FROM ubuntu:latest AS ubuntu_base

WORKDIR /root

# opencascade
RUN  ln -fs /usr/share/zoneinfo/Europe/Paris /etc/localtime \
    && DEBIAN_FRONTEND="noninteractive" \
    && apt-get update \
    && apt-get install -y --no-install-recommends \
        ca-certificates \
        cmake \
        g++ gcc\
        gfortran \
        tcl-dev \
        tk-dev \
        wget \
        libgl1-mesa-dev \
        libxi-dev \
        libxmu-dev \
        && rm -rf /var/lib/apt/lists/* \
    && wget https://github.com/tanatloc/Gmsh-docker/releases/download/0/opencascade-7.4.0.tgz \
        && tar xf opencascade-7.4.0.tgz && cd opencascade-7.4.0  \
        && mkdir build \
        && cd build \
        && cmake .. \
        && make \
        && make install && cd ../.. && rm opencascade-7.4.0.tgz && rm -r opencascade-7.4.0 \
    && DEBIAN_FRONTEND="interactive"

# Compilers amd some gmsh/occ dependencies
RUN apt-get update && apt-get install -y --no-install-recommends \
        git \
        libblas-dev \
        liblapack-dev \
        mesa-common-dev \
        libgl1-mesa-glx \
        libglu1-mesa-dev \
        freeglut3-dev \
        mesa-common-dev \
        wget \
        mesa-utils \ 
        libfltk1.3-dev \
        && rm -rf /var/lib/apt/lists/*
# GMSH installation
RUN  git clone https://gitlab.onelab.info/gmsh/gmsh.git \
        && cd gmsh \
        && mkdir build \
        && cd build \
        && cmake .. \
        && make  \
        && make install && cd ../../ && rm -r gmsh

# Python, clang and some utility packages
RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        wget \
        ssh \
        libssl-dev \
        clang\
        libsuitesparse-dev \
        libarpack2 \
        libarpack2-dev \
        python3-pip python3-dev \
        cmake-curses-gui \
        curl \
        valgrind \
        locales \
    # Set the locale
    && sed -i -e 's/# en_US.UTF-8 UTF-8/en_US.UTF-8 UTF-8/' /etc/locale.gen \
    && locale-gen \
    && curl -fLo /usr/local/bin/yadm https://github.com/TheLocehiliosan/yadm/raw/master/yadm && chmod a+x /usr/local/bin/yadm \
    && rm -rf /var/lib/apt/lists/* \
    && pip3 --no-cache-dir install pytest wheel setuptools scipy matplotlib pandas\
    && git clone https://github.com/hpddm/hpddm.git

# Set the locale https://stackoverflow.com/a/28406007/5913047   
ENV LANG en_US.UTF-8  
ENV LANGUAGE en_US:en  
ENV LC_ALL en_US.UTF-8  

FROM ubuntu_base AS ubuntu_openmpi

WORKDIR /root

RUN apt-get update \
    && apt-get install -y  --no-install-recommends openmpi-bin libopenmpi-dev \
    && rm -rf /var/lib/apt/lists/*

FROM ubuntu_base AS ubuntu_mpich

WORKDIR /root

RUN apt-get update \
    && apt-get install -y  --no-install-recommends mpich libmpich-dev \
    && rm -rf /var/lib/apt/lists/*
