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
yum -y install epel-release centos-release-scl;\
yum -y install https://download.postgresql.org/pub/repos/yum/reporpms/EL-7-x86_64/pgdg-redhat-repo-latest.noarch.rpm;\
yum -y install make automake autoconf scl-utils devtoolset-8-gcc-c++ devtoolset-8-gdb postgresql11-devel postgresql11 openssl-devel zlib-devel python-devel mlocate diffutils patch vim iproute net-tools  bzip2 cifs-utils cmake;\
yum clean all;\
echo 'rt20dev88' | passwd --stdin root;\
ssh-keygen -A;\
sed -i -r 's/^(.*pam_nologin.so)/#\1/' /etc/pam.d/sshd;\
systemctl enable sshd.service;

#是否默认启用devtoolset-8
RUN echo 'source scl_source enable devtoolset-8' >> ~/.bashrc

EXPOSE 22
VOLUME [ "/sys/fs/cgroup" ]
CMD ["/usr/sbin/init"]
