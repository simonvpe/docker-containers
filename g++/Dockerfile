FROM ubuntu:zesty
RUN apt-get update        -yqq                             \
    && apt-get install    -yqq git                         \
    && apt-get install    -yqq software-properties-common  \
    && add-apt-repository -y   ppa:ubuntu-toolchain-r/test \
    && apt-get update     -yqq                             \
    && apt-get install    -yqq g++-7                       \
    && apt-get install    -yqq cmake                       \
    && apt-get install    -yqq libboost1.63-all-dev        \
    && apt-get clean

    


