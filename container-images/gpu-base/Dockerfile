FROM nvidia/cuda:7.5-devel

# OpenCL, OpenGL

RUN apt-get update && \
    apt-get -y install curl git python clinfo nvidia-opencl-icd-352 \
                       mesa-utils libxrandr-dev libxcursor-dev libglew-dev libglu1-mesa-dev libfreeimage-dev libxinerama-dev xinput libxi-dev cmake unzip && \
    rm -rf /var/lib/apt/lists/*

RUN echo "export CPLUS_INCLUDE_PATH=/usr/local/cuda/include;export LIBRARY_PATH=/usr/local/cuda/lib64;export LD_LIBRARY_PATH=/usr/local/cuda/lib64:$LD_LIBRARY_PATH;export PATH=/usr/local/cuda/bin:$PATH;export C_INCLUDE_PATH=/usr/local/cuda/include" >> /etc/profile.d/cuda-libs.sh

WORKDIR /
RUN git clone https://github.com/glfw/glfw.git && pushd glfw && bash -l -c 'cmake -G "Unix Makefiles" -DCMAKE_INSTALL_PREFIX=/usr -DBUILD_SHARED_LIBS=TRUE && make && make install' && popd

CMD clinfo
