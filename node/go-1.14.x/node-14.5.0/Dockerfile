FROM golang:1.14

LABEL maintainer="Chengkun Kang <chengkun.kang@sanofi.com>"

ENV GOPATH /go
ENV HTTP_PROXY "http://7.40.23.198:3128"
ENV HTTPS_PROXY "http://7.40.23.198:3128"

RUN set -x \
    && go get -u -v github.com/revel/revel \
    && go get -u -v github.com/revel/cmd/revel \
    && go get -u github.com/jinzhu/copier \
    && go get -u github.com/golang/protobuf/proto \
    && go get -u github.com/globalsign/mgo/bson \
    && go get -u github.com/lujiacn/revpage \
    && go get -u github.com/lujiacn/utils \
    && go get -u github.com/lujiacn/revauth \
    && go get -u github.com/lujiacn/revel-csrf \
    && go get -u github.com/teris-io/shortid \ 
    && go get -u github.com/tealeg/xlsx \
    && go get -u google.golang.org/grpc \
    && go get -u gopkg.in/lujiacn/mgodo.v0

# Install node
ENV NODE_VERSION "14.5.0"
ENV NODE_ZIP "node-v$NODE_VERSION-linux-x64.tar.gz"

RUN curl -SLO https://nodejs.org/dist/v$NODE_VERSION/$NODE_ZIP && \
    tar -xzf "$NODE_ZIP" -C /usr/local --strip-components 1 && \
    rm "$NODE_ZIP" && \
    node -v && npm -v && revel version

# clear apt cache and remove unnecessary packages
# RUN apt-get autoclean && apt-get -y autoremove

WORKDIR $GOPATH
EXPOSE 9000
