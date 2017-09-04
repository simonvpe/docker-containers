FROM ubuntu:16.04

RUN apt-get update && apt-get install -y ruby-full git inotify-tools \
    && gem install bundler \
    && rm -rf /var/lib/apt/lists/*
    
VOLUME /work
WORKDIR /work
ADD entrypoint /
ENTRYPOINT [ "/entrypoint" ]
