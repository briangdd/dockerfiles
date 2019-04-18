
# Run expressvpn and transmission in a container

FROM polkaned/expressvpn:latest
LABEL maintainer "benjamin@polkaned.net"

RUN apt-get update && apt-get install -y \
    transmission-daemon git nano python wget \
    && wget https://pypi.python.org/packages/source/C/Cheetah/Cheetah-2.4.4.tar.gz \
    && tar -zxvf Cheetah-2.4.4.tar.gz \
    && ./Cheetah-2.4.4/python setup.py install \
    && wget --no-check-certificate https://github.com/midgetspy/Sick-Beard/tarball/master \
    && rm -rf /var/lib/apt/lists/* 
    

CMD ["/usr/bin/transmission-daemon", "--foreground", "--encryption-preferred", "--incomplete-dir", "/var/lib/transmission-daemon/downloads", "--dht", "--download-dir", "/var/lib/transmission-daemon/downloads","--allowed","127.0.0.*,192.168.*.*,172.17.*.*","--config-dir","/var/lib/transmission-daemon/downloads"]
