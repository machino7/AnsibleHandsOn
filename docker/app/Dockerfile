# Pull base image
ARG BASE_IMAGE_TAG
FROM ubuntu:${BASE_IMAGE_TAG}

# Install openssh-server
RUN \
    apt-get update && \
    apt-get install -y openssh-server

RUN mkdir /var/run/sshd && \
    echo 'root:screencast' | chpasswd && \
    sed -i 's/PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config

ENV NOTVISIBLE "in users profile"
RUN echo "export VISIBLE=now" >> /etc/profile

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]

WORKDIR /workspace
