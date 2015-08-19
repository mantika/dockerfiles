FROM python:2.7-slim

RUN mkdir -p /root/.ssh
RUN apt-get update && apt-get install -y git build-essential

COPY builder.pem /root/.ssh/id_rsa
RUN chmod 700 /root/.ssh/id_rsa

RUN git config --global url.ssh://git@github.com/.insteadOf https://github.com/

ONBUILD RUN ssh-keyscan -H github.com > /root/.ssh/known_hosts
ONBUILD COPY . /app/src
