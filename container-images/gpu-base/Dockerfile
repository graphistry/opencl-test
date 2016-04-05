FROM nvidia/cuda:7.5-devel
RUN apt-get update

# OpenCL, OpenGL

RUN apt-get -y install curl git python clinfo nvidia-opencl-icd-352
RUN apt-get install -y mesa-utils libxrandr-dev libxcursor-dev libglew-dev libglu1-mesa-dev libfreeimage-dev libxinerama-dev xinput libxi-dev cmake unzip

RUN echo "export CPLUS_INCLUDE_PATH=/usr/local/cuda/include;export LIBRARY_PATH=/usr/local/cuda/lib64;export LD_LIBRARY_PATH=/usr/local/cuda/lib64:$LD_LIBRARY_PATH;export PATH=/usr/local/cuda/bin:$PATH;export C_INCLUDE_PATH=/usr/local/cuda/include" >> /etc/profile.d/cuda-libs.sh

WORKDIR /
RUN git clone https://github.com/glfw/glfw.git
WORKDIR glfw
RUN bash -l -c 'cmake -G "Unix Makefiles" -DCMAKE_INSTALL_PREFIX=/usr -DBUILD_SHARED_LIBS=TRUE && make && make install'

CMD clinfo
