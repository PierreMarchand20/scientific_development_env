FROM pierremarchand/htool_testing_environments:ubuntu_gcc_openmpi AS ubuntu_gcc_openmpi

WORKDIR /root
USER root

RUN  apt-get update \
    && apt-get install -y --no-install-recommends \
    gdb valgrind yadm zsh fonts-powerline \
    && rm -rf /var/lib/apt/lists/* \
    && chsh -s $(which zsh)

WORKDIR /home/mpi
USER mpi

FROM pierremarchand/htool_testing_environments:ubuntu_gcc_mpich AS ubuntu_gcc_mpich

WORKDIR /root
USER root

# opencascade
RUN  apt-get update \
    && apt-get install -y --no-install-recommends \
    gdb valgrind yadm zsh fonts-powerline \
    && rm -rf /var/lib/apt/lists/* \
    && chsh -s $(which zsh)

WORKDIR /home/mpi
USER mpi

FROM pierremarchand/htool_testing_environments:ubuntu_gcc_mpich AS ubuntu_clang_openmpi

WORKDIR /root
USER root

# opencascade
RUN  apt-get update \
    && apt-get install -y --no-install-recommends \
    gdb valgrind yadm zsh fonts-powerline \
    && rm -rf /var/lib/apt/lists/* \
    && chsh -s $(which zsh)

WORKDIR /home/mpi
USER mpi

FROM pierremarchand/htool_testing_environments:ubuntu_gcc_mpich AS ubuntu_clang_mpich

WORKDIR /root
USER root

# opencascade
RUN  apt-get update \
    && apt-get install -y --no-install-recommends \
    lldb valgrind yadm zsh fonts-powerline \
    && rm -rf /var/lib/apt/lists/* \
    && chsh -s $(which zsh)

WORKDIR /home/mpi
USER mpi
