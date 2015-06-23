FROM alpine:3.2

RUN apk add --update \
    python \
    python-dev \
    py-pip \
    openssh-client \
    git \
    build-base \
  && pip install virtualenv \
  && rm -rf /var/cache/apk/*
