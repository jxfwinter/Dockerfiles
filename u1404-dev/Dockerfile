FROM ubuntu:14.04

RUN apt-get update && apt-get install -y openssh-server vim net-tools iputils-ping lsb-core sudo python cifs-utils build-essential

RUN echo 'root:rt20dev88' | chpasswd

RUN sed -i 's/PermitRootLogin without-password/PermitRootLogin yes/g' /etc/ssh/sshd_config && \
	sed -ri 's/UsePAM yes/UsePAM no/g' /etc/ssh/sshd_config

RUN mkdir /var/run/sshd

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
