FROM centos:8
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

RUN dnf -y install openssl openssh-server dnf-utils
RUN dnf -y install https://download.postgresql.org/pub/repos/yum/reporpms/EL-8-x86_64/pgdg-redhat-repo-latest.noarch.rpm
RUN dnf -qy module disable postgresql
RUN dnf -y install gcc-c++ gdb make automake autoconf cmake
RUN dnf -y install postgresql12-devel postgresql12 python2 python2-devel
RUN dnf -y install openssl-devel libcurl-devel zlib-devel
RUN dnf -y install mlocate patch vim iproute net-tools  bzip2 cifs-utils passwd
RUN dnf -y install glibc-locale-source glibc-langpack-zh
RUN dnf clean all
RUN localedef -c -f UTF-8 -i zh_CN zh_CN.utf8;\
export LANG=zh_CN.UTF-8;\
echo 'LANG="zh_CN.UTF-8"' > /etc/locale.conf;\
echo "export LANG=zh_CN.UTF-8" >> /etc/profile;

RUN echo 'rt20dev88' | passwd --stdin root;\
ssh-keygen -A;\
sed -i -r 's/^(.*pam_nologin.so)/#\1/' /etc/pam.d/sshd;\
systemctl enable sshd.service;

ENV LANG zh_CN.UTF-8
ENV LC_ALL zh_CN.UTF-8

EXPOSE 22
VOLUME [ "/sys/fs/cgroup" ]
CMD ["/usr/sbin/init"]
