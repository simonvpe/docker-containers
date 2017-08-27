FROM ubuntu:16.04

RUN apt-get update -y \
    && echo "Installing needed packages" \
    && apt-get install -y build-essential \
                          mercurial \
			  wget \
			  libmpc-dev \
			  sudo \
			  libbison-dev \
			  flex \
			  autoconf \
			  automake \
			  git \
			  curl \
			  libpng16-dev \
			  libtool \
			  pngquant \
			  cmake \
			  libxml2-dev \
			  pkg-config \
			  gettext \
			  libmount-dev \
			  libmpeg2-4-dev \
			  zip \
			  libsdl2-dev \
			  libreadline-dev \
			  libopenal-dev \
    && rm -rf /var/lib/apt/lists/* \
\
    && echo "Installing atari browner GCC" \
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
        && rm -rf bigbrownbuild \
	&& rm -rf brownout \
\
    && echo "Installing lha" \
        && git clone https://github.com/jca02266/lha.git \
        && cd lha && aclocal && autoheader && automake -a && autoconf \
        && ./configure && make && make install \
        && cd .. && rm -rf lha \
\
    && echo "Installing tmx" \
        && git clone https://github.com/baylej/tmx.git \
        && cd tmx && mkdir build && cd build \
        && cmake .. && make install && cd ../.. \
        && rm -rf tmx \
\
    && echo "Installing vlink" \
        && curl -OL http://sun.hasenbraten.de/vlink/release/vlink.tar.gz \
        && tar zxvf vlink.tar.gz && cd vlink && make \
        && cp vlink /usr/bin/ \
        && cd .. && rm -rf vlink && rm -rf vlink.tar.gz \
\
    && echo "Installing vasm" \
        && curl -OL http://sun.hasenbraten.de/vasm/release/vasm.tar.gz \
        && tar zxvf vasm.tar.gz && cd vasm && make CPU=m68k SYNTAX=mot \
        && cp vasmm68k_mot /usr/bin/ \
        && cd .. && rm -rf vasm && rm -rf vasm.tar.gz \
\
    && echo "Installing libffi" \
        && curl -OL ftp://sourceware.org/pub/libffi/libffi-3.2.1.tar.gz \
        && tar zxvf libffi-3.2.1.tar.gz && cd libffi-3.2.1 \
        && autoreconf -i && ./configure && make -j8 install \
        && cd .. && rm -rf libffi* \
	&& ldconfig \
\
    && echo "Installing pcre" \
       && curl -OL ftp://ftp.csx.cam.ac.uk/pub/software/programming/pcre/pcre-8.38.tar.gz \
       && tar zxvf pcre-8.38.tar.gz && cd pcre-8.38 && autoreconf -i \
       && ./configure --enable-utf --enable-unicode-properties && make -j8 install \
       && cd .. && rm -rf pcre* \
       && ldconfig \
\
    && echo "Installing glib" \
       && curl -OL http://ftp.gnome.org/pub/gnome/sources/glib/2.52/glib-2.52.3.tar.xz \
       && tar xvf glib-2.52.3.tar.xz && cd glib-2.52.3 && autoreconf -i \
       && ./configure && make -j8 install \
       && cd .. && rm -rf glib* \
\
    && echo "Installing (patched) fs-uae" \
       && git clone https://github.com/alpine9000/fs-uae.git \
       && cd fs-uae && ./bootstrap \
       && sed 's/prefix=\/usr\/local/prefix=\/usr/' readline.pc >/usr/lib/pkgconfig/readline.pc \
       && ./configure --with-readline --enable-debug-symbols && make -j8 install \
       && cd .. && rm -rf fs-uae


