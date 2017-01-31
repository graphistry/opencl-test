FROM nvidia/cuda:8.0-devel-ubuntu14.04
RUN DEBIAN_FRONTEND=noninteractive sh -c "apt-get update && apt-get install -y nvidia-opencl-icd-367 g++ && rm -rf /var/lib/apt/lists/*"
ENV CPLUS_INCLUDE_PATH=/usr/local/cuda/include LIBRARY_PATH=/usr/local/cuda/lib64 LD_LIBRARY_PATH=/usr/local/cuda/lib64:$LD_LIBRARY_PATH PATH=/usr/local/cuda/bin:$PATH C_INCLUDE_PATH=/usr/local/cuda/include
