FROM python:2.7.10


RUN mkdir -p /root/.ssh

COPY builder.pem /root/.ssh/id_rsa
RUN chmod 701 /root/.ssh/id_rsa

RUN git config --global url.ssh://git@github.com/.insteadOf https://github.com/

ONBUILD RUN ssh-keyscan -H github.com > /root/.ssh/known_hosts
ONBUILD COPY . /app/src
ONBUILD RUN pip install -r /app/requirements.txt -t /app/dep
