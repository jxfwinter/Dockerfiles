FROM ubuntu:18.04

RUN apt-get update && apt-get install -y openssh-server vim net-tools iputils-ping lsb-core sudo python cifs-utils automake make gcc-8 g++-8 gdb cmake

RUN echo 'root:rt20dev88' | chpasswd

RUN sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/g' /etc/ssh/sshd_config

RUN mkdir /var/run/sshd

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
