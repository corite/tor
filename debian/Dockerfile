FROM debian:latest

RUN apt install -y apt-transport-https
RUN mkdir -p /etc/apt/sources.list.d/
RUN echo "deb     [signed-by=/usr/share/keyrings/tor-archive-keyring.gpg] https://deb.torproject.org/torproject.org $(env -i bash -c '. /etc/os-release; echo $VERSION_CODENAME') main" >> /etc/apt/sources.list.d/tor.list
RUN echo "deb-src [signed-by=/usr/share/keyrings/tor-archive-keyring.gpg] https://deb.torproject.org/torproject.org $(env -i bash -c '. /etc/os-release; echo $VERSION_CODENAME') main" >> /etc/apt/sources.list.d/tor.list

RUN wget -qO- https://deb.torproject.org/torproject.org/A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89.asc | gpg --dearmor | tee /usr/share/keyrings/tor-archive-keyring.gpg >/dev/null

RUN apt update
RUN apt install -y tor

# your torrc goes here
VOLUME /etc/tor

ENTRYPOINT systemctl restart tor@default