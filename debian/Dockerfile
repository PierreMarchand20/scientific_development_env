FROM pierremarchand/htool_testing_environments:debian_gcc_openmpi AS debian_gcc_openmpi

WORKDIR /root
USER root

RUN  apt-get update \
    && apt-get install -y --no-install-recommends \
    gdb yadm \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /home/mpi
USER mpi

FROM pierremarchand/htool_testing_environments:debian_gcc_mpich AS debian_gcc_mpich

WORKDIR /root
USER root

# opencascade
RUN  apt-get update \
    && apt-get install -y --no-install-recommends \
    gdb yadm \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /home/mpi
USER mpi

FROM pierremarchand/htool_testing_environments:debian_gcc_mpich AS debian_clang_openmpi

WORKDIR /root
USER root

# opencascade
RUN  apt-get update \
    && apt-get install -y --no-install-recommends \
    gdb yadm \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /home/mpi
USER mpi

FROM pierremarchand/htool_testing_environments:debian_gcc_mpich AS debian_clang_mpich

WORKDIR /root
USER root

# opencascade
RUN  apt-get update \
    && apt-get install -y --no-install-recommends \
    lldb yadm \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /home/mpi
USER mpi
