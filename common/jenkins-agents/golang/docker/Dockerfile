FROM opendevstackorg/ods-jenkins-agent-base-centos7:latest

LABEL maintainer="Michael Sauter <michael.sauter@boehringer-ingelheim.com>"

ENV GO_VERSION 1.14.2

RUN yum install -y gcc gcc-c++

RUN cd /tmp && \
    curl -LO https://storage.googleapis.com/golang/go$GO_VERSION.linux-amd64.tar.gz && \
    tar -C /usr/local -xzf go$GO_VERSION.linux-amd64.tar.gz && \
    rm -f *.tar.gz && \
    cd - && \
    mkdir /go

ENV PATH $PATH:/usr/local/go/bin
ENV GOBIN /usr/local/bin

RUN curl -sSfL https://raw.githubusercontent.com/golangci/golangci-lint/master/install.sh | sh -s -- -b /usr/local/bin v1.25.0

RUN go get -u github.com/jstemmer/go-junit-report

RUN mkdir -p /home/jenkins/go && chmod g+w /home/jenkins/go

WORKDIR /go
