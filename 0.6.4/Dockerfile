FROM debian:wheezy

MAINTAINER toph <toph@toph.fr>

RUN \
    apt-get update && \
    apt-get install -y ruby libsqlite3-0 --no-install-recommends && \
    rm -rf /var/lib/apt/lists/* && \
    true

ENV MAILCATCHER_VERSION 0.6.4

RUN \
    buildDeps=" \
        ruby-dev \
        build-essential \
        libsqlite3-dev \
    " && \
    apt-get update && apt-get install -y $buildDeps --no-install-recommends && rm -rf /var/lib/apt/lists/* && \
    gem install -v $MAILCATCHER_VERSION mailcatcher --no-ri --no-rdoc && \
    apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false -o APT::AutoRemove::SuggestsImportant=false $buildDeps && \
    rm -rf /var/lib/apt/lists/* && \
    true

EXPOSE 25 80

CMD ["mailcatcher", "--foreground", "--ip=0.0.0.0", "--smtp-port=25", "--http-port=80"]
