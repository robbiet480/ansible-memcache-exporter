# building linux-amd64 native binary via Dockerized Go compiler
#
# @see https://registry.hub.docker.com/_/golang/
#

# pull base image
FROM golang:1.4.2
MAINTAINER Robbie Trencheny <me@robbiet.us>


ENV PROJECT_REPO  github.com/Snapbug/memcache_exporter
ENV EXE_NAME      memcache_exporter-linux-amd64

ENV GOPATH        /opt
ENV PATH          $GOPATH/bin:$PATH
WORKDIR           /opt


RUN echo "===> Fetch and build aux tool: go-bindata ..."
RUN go get -u github.com/jteeuwen/go-bindata             
RUN cd /opt/src/github.com/jteeuwen/go-bindata   && \
    make                                                  


RUN echo "===> Fetch and build main project..."
RUN go get -u $PROJECT_REPO
RUN cd /opt/src/$PROJECT_REPO  && \
    make build


# copy executable...
RUN      mkdir -p /dist
VOLUME   [ "/dist" ]
CMD      cp  $GOPATH/src/$PROJECT_REPO/memcache_exporter  /dist/$EXE_NAME
