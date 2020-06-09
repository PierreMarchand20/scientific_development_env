# Testing environments for [Htool](https://github.com/PierreMarchand20/htool) [![Docker Automated](https://img.shields.io/docker/cloud/automated/pierremarchand/scientific_development_env.svg)](https://img.shields.io/docker/cloud/automated/pierremarchand/scientific_development_env) [![Docker Build](https://img.shields.io/docker/cloud/build/pierremarchand/scientific_development_env.svg)](https://img.shields.io/docker/cloud/build/pierremarchand/scientific_development_env)

Four environments are defined via Docker images with several MPI implementations:

- Ubuntu with `OpenMPI`
- Ubuntu with `MPICH`
- Debian with `OpenMPI`
- Debian with `MPICH`

These are for my personal use, but feel free to use it, and to look at it to build your own images.

The Docker images can be pulled from [Docker Hub](https://hub.docker.com/repository/docker/pierremarchand/scientific_development_env).

Note that we use `docker-compose` to factorize as much as possible the definition of the environments, so that we had to override the `build` and `push` hooks of Docker Hub for automated build.
