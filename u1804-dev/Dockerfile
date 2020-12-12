FROM ubuntu:18.04

RUN apt-get update && apt-get install -y openssh-server vim net-tools iputils-ping lsb-core sudo python cifs-utils automake make gcc-8 g++-8 gdb

RUN curl -L -OJ https://github.com/Kitware/CMake/releases/download/v3.19.1/cmake-3.19.1-Linux-x86_64.sh
RUN sh cmake-3.19.1-Linux-x86_64.sh --prefix=/usr/local --exclude-subdir --skip-license
RUN rm -rf cmake-3.19.1-Linux-x86_64.sh

RUN echo 'root:rt20dev88' | chpasswd

RUN sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/g' /etc/ssh/sshd_config

RUN mkdir /var/run/sshd

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
