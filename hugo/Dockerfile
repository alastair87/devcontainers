FROM docker.io/alastair87/debian:latest
USER root
ADD https://github.com/gohugoio/hugo/releases/download/v0.122.0/hugo_extended_0.123.1_linux-amd64.deb /tmp/hugo_extended.deb 
RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y /tmp/hugo_extended.deb && \
    apt-get autoclean && \
    rm /tmp/hugo_extended.deb
USER user
