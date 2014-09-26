FROM koelnconcert/devbox-base
MAINTAINER Sebastian Peters <koelnconcert@googlemail.com>

USER root
# packages split for better performance on adding packages
RUN apt-get update -y && apt-get install -y \
    openjdk-7-jdk
RUN apt-get update -y && apt-get install -y \
    ant \
    maven2
USER dev

