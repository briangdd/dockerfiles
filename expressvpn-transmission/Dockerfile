
# Run expressvpn and transmission in a container

FROM polkaned/expressvpn:latest
LABEL maintainer "benjamin@polkaned.net"
#
#RUN apt-get update && apt-get install -y \
#    git-core python python-cheetah \
#   transmission-daemon nano python wget \
#    && cd ~ && git clone https://github.com/briangdd/sickrage.git .sickrage \
#    && cd ~/.sickrage \
#    && ls -l \
#    && cp -a sickrage/autoProcessTV/autoProcessTV.cfg.sample sickrage/autoProcessTV/autoProcessTV.cfg
    
RUN apt-get update && apt-get install -y \
    git-core python python-cheetah \
    python-pip \
    transmission-daemon nano wget \
    && pip install pyopenssl \
    &&  mkdir /app /var/run/sickchill \
    &&  cd ~ && git clone https://github.com/sickchill/sickchill.git .sickchill 

COPY . /app/sickchill

WORKDIR /app/sickchill

VOLUME /data /downloads /tv



EXPOSE 8088
    

CMD ["/usr/bin/transmission-daemon",\
"--foreground", \
"--encryption-preferred", \
"--incomplete-dir", \
"/var/lib/transmission-daemon/downloads", \
"--dht", \
"--download-dir", \
"/var/lib/transmission-daemon/downloads", \
"--allowed","127.0.0.*,192.168.*.*,172.17.*.*", \
"--config-dir","/var/lib/transmission-daemon/downloads", \
"&&", \
"/usr/local/bin/python","SickBeard.py","-q", "--nolaunch","--datadir=/data","--port" 8088"]
