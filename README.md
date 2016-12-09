# Graphistry Infrastructure

We are excited to share our infrastructure automation, and hope that it will be useful to you. We are enthusiastic about artifact-based workflows, and our artifacts are Docker containers that run our OpenCL code.

## Install docker & nvidia-docker on a machine

* [Ubuntu setup](https://github.com/graphistry/infrastructure/tree/master/nvidia-docker-host)
* [RHEL setup](https://github.com/graphistry/infrastructure/tree/master/nvidia-docker-rhel)

## Build off of our containers

* [Base OpenCL-on-the-GPU container](https://hub.docker.com/r/graphistry/gpu-base/)

* [`node-opencl` GPU container](https://hub.docker.com/r/graphistry/js-gpu/)

* [`node-opencl` CPU container](https://hub.docker.com/r/graphistry/cpu-base/)

### Usage example in an open-source `node-opencl` library

* [`cljs`](https://github.com/graphistry/cljs)
