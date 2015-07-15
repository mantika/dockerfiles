FROM python:2.7.10-slim 

RUN apt-get update
RUN apt-get install -y python-dev python-numpy python-scipy git
RUN pip install --upgrade --no-deps git+git://github.com/Theano/Theano.git
RUN pip install six

ENV PYTHONPATH /usr/lib/python2.7/dist-packages/:$PYTHONPATH

RUN mkdir -p /root/.ssh

COPY builder.pem /root/.ssh/id_rsa
RUN chmod 700 /root/.ssh/id_rsa

RUN git config --global url.ssh://git@github.com/.insteadOf https://github.com/

ONBUILD RUN ssh-keyscan -H github.com > /root/.ssh/known_hosts
ONBUILD COPY . /app/src
