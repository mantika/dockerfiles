FROM golang:1.6.3-wheezy

RUN mkdir -p /root/.ssh
RUN mkdir -p /go/src/app
WORKDIR /go/src/app

COPY builder.pem /root/.ssh/id_rsa
RUN chmod 700 /root/.ssh/id_rsa

RUN git config --global url.ssh://git@github.com/.insteadOf https://github.com/

ONBUILD RUN ssh-keyscan -H github.com > /root/.ssh/known_hosts
