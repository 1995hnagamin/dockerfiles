FROM ubuntu:14.04
WORKDIR /
RUN apt-get update && apt-get install -y build-essential libboost-all-dev libxml2-dev make pkg-config --no-install-recommends
RUN \
 apt-get install -y clang cmake curl file python ninja-build xz-utils --no-install-recommends && \
 curl http://releases.llvm.org/3.6.2/llvm-3.6.2.src.tar.xz | tar xJf - && \
 mv /llvm-3.6.2.src /llvm && \
 curl http://releases.llvm.org/3.6.2/compiler-rt-3.6.2.src.tar.xz | tar xJf - && \
 mv /compiler-rt-3.6.2.src /llvm/projects/compiler-rt && \
 curl http://releases.llvm.org/3.6.2/cfe-3.6.2.src.tar.xz | tar xJf - && \
 mv /cfe-3.6.2.src /llvm/tools/clang && \
 mkdir llvm/build
RUN \
 cd llvm/build && \
 CC=clang CXX=clang++ cmake -G Ninja .. && \
 (ninja || ninja -j1)
RUN \
 cd llvm/build && \
 ninja install && \
 rm -rf /llvm /build
