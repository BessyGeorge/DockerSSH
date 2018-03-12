FROM ubuntu
ARG SSH_KEY_PUB
RUN echo "$SSH_KEY_PUB"
RUN apt-get -y update && \
    apt-get install -y openssh-server libssl-dev && \
    mkdir -p /var/run/sshd && \
    mkdir -p /root/.ssh && \
    chmod 0700 /root/.ssh && \
    echo "$SSH_KEY_PUB" >> /root/.ssh/authorized_keys && \
    service ssh restart
EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
