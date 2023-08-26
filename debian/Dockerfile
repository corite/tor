FROM debian:latest

RUN apt install apt-transport-https lsb_release
RUN mkdir -p /etc/apt/sources.list.d/
RUN echo "deb     [signed-by=/usr/share/keyrings/tor-archive-keyring.gpg] https://deb.torproject.org/torproject.org $(lsb_release -c) main" >> /etc/apt/sources.list.d/tor.list
RUN echo "deb-src [signed-by=/usr/share/keyrings/tor-archive-keyring.gpg] https://deb.torproject.org/torproject.org $(lsb_release -c) main" >> /etc/apt/sources.list.d/tor.list
RUN apt purge lsb_release

RUN wget -qO- https://deb.torproject.org/torproject.org/A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89.asc | gpg --dearmor | tee /usr/share/keyrings/tor-archive-keyring.gpg >/dev/null

RUN apt update
RUN apt install tor deb.torproject.org-keyring

# your torrc goes here
VOLUME /etc/tor

ENTRYPOINT systemctl restart tor@default