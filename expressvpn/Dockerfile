
# Run expressvpn in a container

FROM debian:buster-slim
LABEL maintainer "benjamin@polkaned.net"

ENV ACTIVATION_CODE Code
ENV LOCATION smart
ARG APP=expressvpn_2.0.0-1_amd64

RUN apt-get update && apt-get install -y --no-install-recommends \
    ca-certificates wget expect iproute2 \
    && rm -rf /var/lib/apt/lists/* \
    && wget -q "https://download.expressvpn.xyz/clients/linux/${APP}" -O /tmp/${APP} \
    && dpkg -i /tmp/${APP} \
    && rm -rf /tmp/*.deb \
    && apt-get purge -y --auto-remove wget

COPY entrypoint.sh /tmp/entrypoint.sh
COPY expressvpnActivate.sh /tmp/expressvpnActivate.sh

ENTRYPOINT ["/usr/bin/bash", "/tmp/entrypoint.sh"]