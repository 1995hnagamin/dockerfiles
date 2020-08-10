FROM ubuntu:20.04
WORKDIR /
ENV TZ=Asia/Tokyo
ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update -y && apt-get upgrade -y
RUN apt-get install -y tzdata
RUN apt-get install -y build-essential ca-certificates clang cmake curl file python ninja-build wget xz-utils --no-install-recommends && \
 wget https://github.com/llvm/llvm-project/releases/download/llvmorg-10.0.1/llvm-10.0.1.src.tar.xz && \
 tar xJf llvm-10.0.1.src.tar.xz && \
 mv /llvm-10.0.1.src /llvm && \
 rm /llvm-10.0.1.src.tar.xz && \
 wget https://github.com/llvm/llvm-project/releases/download/llvmorg-10.0.1/compiler-rt-10.0.1.src.tar.xz && \
 tar xJf compiler-rt-10.0.1.src.tar.xz && \
 mv /compiler-rt-10.0.1.src /llvm/projects/compiler-rt && \
 rm /compiler-rt-10.0.1.src.tar.xz && \
 wget https://github.com/llvm/llvm-project/releases/download/llvmorg-10.0.1/clang-10.0.1.src.tar.xz && \
 tar xJf clang-10.0.1.src.tar.xz && \
 mv /clang-10.0.1.src /llvm/tools/clang && \
 rm /clang-10.0.1.src.tar.xz && \
 mkdir llvm/build && \
 cd llvm/build && \
 CC=clang CXX=clang++ cmake -G Ninja -DCMAKE_BUILD_TYPE=MinSizeRel -DLLVM_TARGETS_TO_BUILD=X86 .. && \
 (ninja || ninja -j1) && \
 ninja install && \
 rm -rf /llvm /build
