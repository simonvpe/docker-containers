FROM ubuntu:16.04

RUN apt-get update && apt-get install -y ruby-full git \
    && gem install bundler \
    && rm -rf /var/lib/apt/lists/*
    
VOLUME /work
WORKDIR /work
ADD entrypoint /
ADD Gemfile /work
ENTRYPOINT [ "/entrypoint" ]
