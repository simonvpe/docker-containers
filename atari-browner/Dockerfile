FROM ubuntu:16.04

RUN apt-get update -y \
    && apt-get install -y build-essential \
                          mercurial \
			  wget \
			  libmpc-dev \
			  sudo \
			  libbison-dev \
			  flex \
    && apt-get clean \
    && hg clone https://bitbucket.org/ggnkua/brownout \
    && hg clone https://bitbucket.org/ggnkua/bigbrownbuild \
    && cd bigbrownbuild \
    && wget http://mirrors-usa.go-parts.com/gcc/releases/gcc-7.1.0/gcc-7.1.0.tar.bz2 \
    && wget https://ftp.gnu.org/gnu/binutils/binutils-2.27.tar.bz2 \
    && wget http://d-bug.mooo.com/releases/mintlib-CVS-20160320.tar.gz \
    && bash -c "echo a | ./bigbrownbuild.sh" \
    && cd / \
    && tar -jxvf bigbrownbuild/binary-package/binutils-2.27-ataribrowner-bin.tar.bz2 \
    && tar -jxvf bigbrownbuild/binary-package/gcc-7.1-ataribrownerbin.tar.bz2 \
    && cd bigbrownbuild \
    && tar -xvf mintlib-CVS-20160320/mintlib-0.60.1-bin.tar.gz \
    && cd mintlib-0.60.1-bin \
    && cp -r include lib lib020 lib020_soft lib020-60 lib020-60_soft lib040 libv4e \
             /usr/m68k-ataribrowner-elf/ \
    && cd / \ 
    && rm -rf bigbrownbuild



