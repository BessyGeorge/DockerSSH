FROM ubuntu
ADD ssh/id_rsa.pub /root/pub-key
RUN apt-get -y update &&  \
    apt-get install -y openssh-server libssl-dev && \
    mkdir /var/run/sshd && \
    mkdir -p /root/.ssh && \
    echo 'root:admin' | chpasswd && \
    sed -i 's/PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config && \
    sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd && \

    cat /root/pub-key >> /root/.ssh/authorized_keys && \
    chmod 0600 /root/.ssh/authorized_keys &&\
    chmod go-w  ~ && \

    ssh-keygen -t rsa -f ansible_id_rsa && \
    cat ansible_id_rsa >> /root/.ssh/id_rsa && \
    cat ansible_id_rsa.pub >> /root/.ssh/id_rsa.pub && \
    chmod 0644 /root/.ssh/id_rsa.pub && \
    chmod 0700  /root/.ssh/ && \
    service ssh restart 

ENV NOTVISIBLE "in users profile"
RUN echo "export VISIBLE=now" >> /etc/profile

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
