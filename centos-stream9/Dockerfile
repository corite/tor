FROM quay.io/centos/centos:stream9

RUN dnf install -y epel-release
RUN mkdir -p /etc/yum.repos.d
COPY ./centos-stream9/tor.repo /etc/yum.repos.d
RUN dnf install tor

# your torrc goes here
VOLUME /etc/tor

ENTRYPOINT systemctl enable --now tor
