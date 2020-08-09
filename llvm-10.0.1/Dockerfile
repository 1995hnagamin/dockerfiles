FROM ubuntu:20.04
WORKDIR /
RUN apt-get update
RUN apt-get install -y clang cmake curl file python ninja-build xz-utils --no-install-recommends
RUN apt-get install -y ca-certificates wget --no-install-recommends
RUN wget https://github.com/llvm/llvm-project/releases/download/llvmorg-10.0.1/llvm-10.0.1.src.tar.xz
RUN tar xJf llvm-10.0.1.src.tar.xz
RUN mv /llvm-10.0.1.src /llvm
RUN wget https://github.com/llvm/llvm-project/releases/download/llvmorg-10.0.1/compiler-rt-10.0.1.src.tar.xz
RUN tar xJf compiler-rt-10.0.1.src.tar.xz
RUN mv /compiler-rt-10.0.1.src /llvm/projects/compiler-rt
RUN wget https://github.com/llvm/llvm-project/releases/download/llvmorg-10.0.1/clang-10.0.1.src.tar.xz
RUN tar xJf clang-10.0.1.src.tar.xz
RUN mv /clang-10.0.1.src /llvm/tools/clang
RUN mkdir llvm/build
WORKDIR llvm/build
RUN CC=clang CXX=clang++ cmake -G Ninja -DCMAKE_BUILD_TYPE=MinSizeRel -DLLVM_TARGETS_TO_BUILD=X86 ..
RUN (ninja || ninja -j1)
RUN ninja install
RUN rm -rf /llvm /build
