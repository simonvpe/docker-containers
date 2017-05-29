FROM ubuntu:latest

# Install dependencies
RUN apt-get update -y \
    && apt-get install -yqq libssl-dev git-core sudo \
    && apt-get clean

# Install torch and cutorch 1.0-0
RUN git clone https://github.com/torch/distro.git /torch --recursive \
    && cd /torch \
    && /bin/bash install-deps \
    && sed -i 's/cutorch-scm-1.rockspec/cutorch-1.0-0.rockspec/g' install.sh \
    && ./install.sh -b \
    && apt-get clean
