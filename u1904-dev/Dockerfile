FROM ubuntu:19.04

RUN apt-get update && apt-get install -y openssh-server

RUN echo 'root:rt20dev88' | chpasswd

RUN sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/g' /etc/ssh/sshd_config && \
	sed -ri 's/UsePAM yes/UsePAM no/g' /etc/ssh/sshd_config

RUN mkdir /var/run/sshd

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
