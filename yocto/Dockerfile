FROM ubuntu:xenial

RUN apt-get update     -yqq                                            \
    && apt-get install -yqq gawk wget git-core diffstat unzip texinfo  \
                            gcc-multilib build-essential chrpath socat \
                            libsdl1.2-dev xterm python3 locales        \
			    sudo                                       \
    && locale-gen en_US.UTF-8
ENV LANG='en_US.UTF-8' LANGUAGE='en_US:en' LC_ALL='en_US.UTF-8'

