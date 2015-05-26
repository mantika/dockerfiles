FROM golang:1.4.2

RUN mkdir -p /root/.ssh
RUN mkdir -p /go/src/app
WORKDIR /go/src/app

COPY builder.pem /root/.ssh/id_rsa
RUN chmod 700 /root/.ssh/id_rsa

RUN git config --global url.ssh://git@github.com/.insteadOf https://github.com/

# this will ideally be built by the ONBUILD below ;)
CMD ["go-wrapper", "run"]

ONBUILD RUN ssh-keyscan -H github.com > /root/.ssh/known_hosts
ONBUILD COPY . /go/src/app
ONBUILD RUN go-wrapper download
ONBUILD RUN go-wrapper install
