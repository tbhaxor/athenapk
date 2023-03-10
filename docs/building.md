# Build Instructions

## Arch Linux

**Dependencies** cuda, cuda-tools, openmpi, hdf5-openmpi, cmake, make

```sh
wget -O /tmp/clang-format https://github.com/muttleyxd/clang-format-static-binaries/releases/download/master-1d7ec53d/clang-format-14_linux-amd64
chmod +x /tmp/clang-format

cmake -Bbuild-gpu \
    -DKokkos_ARCH_TURING75=ON -DKokkos_ENABLE_OPENMP=ON  -DKokkos_ENABLE_CUDA=ON -DCUDA_ROOT=/opt/cuda \
    -DCMAKE_CXX_COMPILER=/usr/bin/clang++ -DCMAKE_CXX_FLAGS="-I/opt/cuda/targets/x86_64-linux/include/ -L/opt/cuda/targets/x86_64-linux/lib/" \
    -DCLANG_FORMAT=/tmp/clang-format
```