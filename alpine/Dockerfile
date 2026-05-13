ARG ARCH
FROM ${ARCH}/alpine:3.21
LABEL version="3"

ENV DEBIAN_FRONTEND=noninteractive

RUN apk update && \
    apk upgrade

RUN apk add --no-cache python3 py3-pip && \
    if [ ! -e /usr/bin/pip ]; then ln -s pip3 /usr/bin/pip ; fi && \
    if [ ! -e /usr/bin/python ]; then ln -sf /usr/bin/python3 /usr/bin/python; fi

RUN apk add --no-cache \
            build-base linux-headers \
            cmake ninja \
            autoconf automake libtool make \
            openssl openssl-dev python3-dev \
            git docker \
            gmp gmp-dev \
            musl-dev

# Unit testing prereqs
RUN pip3 install --break-system-packages -U pytest-xdist psutil requests

# Setup identical environment for CircleCI
RUN touch /root/.bashrc

CMD ["/bin/sh"]
