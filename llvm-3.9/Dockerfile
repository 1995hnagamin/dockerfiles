FROM ubuntu:16.04
WORKDIR /
RUN apt-get update
RUN apt-get install -y ninja-build cmake clang python curl xz-utils --no-install-recommends
RUN curl http://releases.llvm.org/3.9.1/llvm-3.9.1.src.tar.xz | tar xJf -
RUN mv /llvm-3.9.1.src /llvm
RUN curl http://releases.llvm.org/3.9.1/compiler-rt-3.9.1.src.tar.xz | tar xJf -
RUN mv /compiler-rt-3.9.1.src /llvm/projects/compiler-rt
RUN curl http://releases.llvm.org/3.9.1/cfe-3.9.1.src.tar.xz | tar xJf -
RUN mv /cfe-3.9.1.src /llvm/tools/clang
RUN mkdir llvm/build
WORKDIR llvm/build
RUN CC=clang CXX=clang++ cmake -G Ninja ..
RUN ninja
RUN ninja install
RUN rm -rf /llvm /build
RUN strip /usr/local/bin/[a-fh-z]*
RUN apt-get remove --auto-remove -y ninja-build cmake clang curl xz-utils
