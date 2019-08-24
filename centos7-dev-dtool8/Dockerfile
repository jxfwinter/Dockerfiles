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
rm -f /lib/systemd/system/anaconda.target.wants/*;\
yum -y install openssl openssh-server yum-utils;\
yum -y install centos-release-scl;\
yum -y install https://download.postgresql.org/pub/repos/yum/reporpms/EL-7-x86_64/pgdg-redhat-repo-latest.noarch.rpm;\
yum -y install kde-l10n-Chinese make automake autoconf scl-utils devtoolset-8-gcc-c++ devtoolset-8-gdb postgresql11-devel postgresql11 openssl-devel zlib-devel python-devel mlocate patch vim iproute net-tools  bzip2 cifs-utils cmake;\
yum -y reinstall glibc-common;\
yum clean all;\
localedef -c -f UTF-8 -i zh_CN zh_CN.utf8;\
export LANG=zh_CN.UTF-8;\
echo 'LANG="zh_CN.UTF-8"' > /etc/locale.conf;\
echo "export LANG=zh_CN.UTF-8" >> /etc/profile;\
echo 'rt20dev88' | passwd --stdin root;\
ssh-keygen -A;\
sed -i -r 's/^(.*pam_nologin.so)/#\1/' /etc/pam.d/sshd;\
systemctl enable sshd.service;

ENV LANG zh_CN.UTF-8
ENV LC_ALL zh_CN.UTF-8

#是否默认启用devtoolset-8
RUN echo 'source scl_source enable devtoolset-8' >> ~/.bashrc

EXPOSE 22
VOLUME [ "/sys/fs/cgroup" ]
CMD ["/usr/sbin/init"]
