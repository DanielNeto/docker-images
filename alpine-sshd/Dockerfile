ARG         ALPINE_VERSION=${ALPINE_VERSION:-3.8}
FROM        alpine:${ALPINE_VERSION}

LABEL       maintainer="https://github.com/DanielNeto"

ARG         OPENSSH_VERSION=${OPENSSH_VERSION:-7.9}
ENV         OPENSSH_VERSION=${OPENSSH_VERSION}

RUN         apk update && \
            apk upgrade && \
            apk add openssh=${OPENSSH_VERSION} && \
            apk add iperf && \
            mkdir -p /root/.ssh && \
            rm -rf /var/cache/apk/* /tmp/*

##Setting root password as root
RUN         echo "root:root" | chpasswd

EXPOSE      22
VOLUME      ["/etc/ssh"]
CMD         /usr/sbin/sshd -D
