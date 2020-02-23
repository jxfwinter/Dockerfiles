FROM centos:7
ENV container docker

RUN (cd /lib/systemd/system/sysinit.target.wants/; for i in *; do [ $i == \
systemd-tmpfiles-setup.service ] || rm -f $i; done); \
rm -f /lib/systemd/system/multi-user.target.wants/*;\
rm -f /etc/systemd/system/*.wants/*;\
rm -f /lib/systemd/system/local-fs.target.wants/*; \
rm -f /lib/systemd/system/sockets.target.wants/*udev*; \
rm -f /lib/systemd/system/sockets.target.wants/*initctl*; \
rm -f /lib/systemd/system/basic.target.wants/*;\
rm -f /lib/systemd/system/anaconda.target.wants/*;

RUN yum -y install openssl openssh-server yum-utils
RUN yum -y install diffutils unzip kde-l10n-Chinese make automake autoconf patch vim iproute net-tools bzip2 cifs-utils cmake tcpdump lsof psmisc
RUN yum -y install gcc-c++ gdb
RUN yum -y reinstall glibc-common

RUN yum-config-manager --add-repo http://www.nasm.us/nasm.repo
RUN yum -y install nasm

RUN yum clean all
RUN localedef -c -f UTF-8 -i zh_CN zh_CN.utf8
RUN export LANG=zh_CN.UTF-8
RUN echo 'LANG="zh_CN.UTF-8"' > /etc/locale.conf
RUN echo "export LANG=zh_CN.UTF-8" >> /etc/profile
RUN echo 'rt20dev88' | passwd --stdin root
RUN ssh-keygen -A
RUN sed -i -r 's/^(.*pam_nologin.so)/#\1/' /etc/pam.d/sshd
RUN systemctl enable sshd.service

ENV LANG zh_CN.UTF-8
ENV LC_ALL zh_CN.UTF-8

EXPOSE 22
VOLUME [ "/sys/fs/cgroup" ]
CMD ["/usr/sbin/init"]
