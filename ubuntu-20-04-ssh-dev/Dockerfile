FROM ubuntu:20.04

ARG DEBIAN_FRONTEND=noninteractive

# Install the most basic requirements

RUN apt-get update && apt-get -y install \
    sudo \
    git \
    nano \
    openssh-server

# Create non-root (sudo) user for development
# user: dev
# passwd: 123

RUN adduser --disabled-password --gecos "" dev && \
    usermod -p $(openssl passwd -1 123) dev && \
    usermod -aG sudo dev

# ssh server port
EXPOSE 22

# switch to 
USER dev

CMD echo "123" | sudo -S service ssh start && /bin/bash