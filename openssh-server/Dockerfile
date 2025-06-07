FROM ubuntu:22.04

ARG SSH_PASSWORD="hiz3nah8neeRais5zuth"

# Install OpenSSH Server
RUN apt-get update && apt-get install -y \
    openssh-server \
    && rm -rf /var/lib/apt/lists/*
RUN mkdir /var/run/sshd
RUN echo "root:${SSH_PASSWORD}" | chpasswd
RUN sed -i \
    -e 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' \
    /etc/ssh/sshd_config
# Ref: https://stackoverflow.com/a/34631891
RUN env | egrep -v "^(HOME=|USER=|MAIL=|LC_ALL=|LS_COLORS=|LANG=|HOSTNAME=|PWD=|TERM=|SHLVL=|LANGUAGE=|_=)" >> /etc/environment

# Ref: https://github.com/serversideup/docker-ssh/blob/main/src/Dockerfile
# -D in CMD below prevents sshd from becoming a daemon. -e is to log everything to stderr.
CMD ["/usr/sbin/sshd", "-D", "-e"]
