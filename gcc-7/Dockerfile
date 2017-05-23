FROM ubuntu:zesty

# Install g++-7, gcc-7 and boost-1.63
RUN apt-get update        -yqq                             \
    && apt-get install    -yqq git                         \
    && apt-get install    -yqq software-properties-common  \
    && add-apt-repository -y   ppa:ubuntu-toolchain-r/test \
    && apt-get update     -yqq                             \
    && apt-get install    -yqq g++-7                       \
    && apt-get install    -yqq gcc-7                       \
    && apt-get install    -yqq libboost1.63-all-dev        \
    && apt-get clean                                       \
    && ln -s /usr/bin/g++-7 /usr/bin/g++                   \
    && ln -s /usr/bin/gcc-7 /usr/bin/gcc

# Install cmake-3.8
RUN apt-get install    -yqq curl                               \
    && apt-get install -yqq build-essential                    \
    && apt-get install -yqq zlib1g-dev                         \
    && apt-get install -yqq libcurl4-gnutls-dev                \
    && apt-get install -yqq libncurses5-dev                    \
    && apt-get install -yqq libarchive-dev                     \
    && curl -O https://cmake.org/files/v3.8/cmake-3.8.1.tar.gz \
    && tar xvf cmake-3.8.1.tar.gz                              \
    && cd cmake-3.8.1                                          \
    && sed -i '/CMAKE_USE_LIBUV 1/s/1/0/' CMakeLists.txt       \
    && sed -i '/"lib64"/s/64//' Modules/GNUInstallDirs.cmake   \
    && ./bootstrap                                             \
         --prefix=/usr                                         \
         --system-libs                                         \
         --mandir=/share/man                                   \
         --no-system-jsoncpp                                   \
         --no-system-librhash                                  \
         --docdir=/share/doc/cmake-3.8.1                       \
    && make -j12 && make install                               \
    && cd .. && rm cmake-3.8.1.tar.gz && rm -rf cmake-3.8.1    \
    && apt-get clean

    


