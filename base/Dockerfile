FROM ubuntu:14.04
MAINTAINER Sebastian Peters <koelnconcert@googlemail.com>

# install base packages for bootstraping dev user
ENV DEBIAN_FRONTEND noninteractive
RUN apt-get update -y && apt-get install -y \
  curl \
  git

# base config
RUN echo "ALL	ALL = (ALL) NOPASSWD: ALL" >> /etc/sudoers

# German settings
RUN cp /usr/share/zoneinfo/Europe/Berlin /etc/localtime
RUN locale-gen de_DE.UTF-8
ENV LC_ALL de_DE.UTF-8

# create dev user
RUN useradd -m dev
WORKDIR /home/dev
ENV HOME /home/dev
USER dev

# install homeshick and dotfiles
RUN curl -Ls https://raw.github.com/koelnconcert/dotfiles/master/install.sh | bash

# config dev user
RUN sed -i -e '/^LP_HOSTNAME_ALWAYS=/ s/=0/=1/' .liquidpromptrc

# install additional packages
#
# putting this to the end to make rebuilding after adding new packages much faster
USER root
RUN apt-get update -y && apt-get install -y \
    byobu \
    dnsutils \
    htop \
    jq \
    make \
    man-db \
    mbuffer \
    moreutils \
    pv \
    xml2 \
    vim \
    wget

# back to dev user
USER dev
