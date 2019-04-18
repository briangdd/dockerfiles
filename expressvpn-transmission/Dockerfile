
# Run expressvpn and transmission in a container

FROM polkaned/expressvpn:latest
LABEL maintainer "benjamin@polkaned.net"

RUN apt-get update && apt-get install -y \
    transmission-daemon git nano python wget \
    && wget https://pypi.python.org/packages/source/C/Cheetah/Cheetah-2.4.4.tar.gz \
    && tar -zxvf Cheetah-2.4.4.tar.gz \
    && cd ./Cheetah-2.4.4 \
    && python setup.py install \
    && cd ..
    && git clone git://github.com/midgetspy/Sick-Beard.git my-sickbeard-install \
    && rm -rf /var/lib/apt/lists/* 
    

CMD ["/usr/bin/transmission-daemon", "--foreground", "--encryption-preferred", "--incomplete-dir", "/var/lib/transmission-daemon/downloads", "--dht", "--download-dir", "/var/lib/transmission-daemon/downloads","--allowed","127.0.0.*,192.168.*.*,172.17.*.*","--config-dir","/var/lib/transmission-daemon/downloads"]
