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
RUN yum -y install centos-release-scl
RUN yum -y install unzip kde-l10n-Chinese make automake autoconf openssl-devel libcurl-devel zlib-devel python-devel mlocate patch vim iproute net-tools bzip2 cifs-utils cmake
RUN yum -y install https://download.postgresql.org/pub/repos/yum/reporpms/EL-7-x86_64/pgdg-redhat-repo-latest.noarch.rpm
RUN yum -y install scl-utils devtoolset-8-gcc-c++ devtoolset-8-gdb 
RUN yum -y install gcc-c++ gdb postgresql-devel
RUN yum -y reinstall glibc-common
RUN yum clean all
RUN localedef -c -f UTF-8 -i zh_CN zh_CN.utf8
RUN export LANG=zh_CN.UTF-8
RUN echo 'LANG="zh_CN.UTF-8"' > /etc/locale.conf
RUN echo "export LANG=zh_CN.UTF-8" >> /etc/profile
RUN echo 'rt20dev88' | passwd --stdin root
RUN ssh-keygen -A
RUN sed -i -r 's/^(.*pam_nologin.so)/#\1/' /etc/pam.d/sshd
RUN systemctl enable sshd.service

RUN curl -L -OJ https://github.com/ninja-build/ninja/releases/download/v1.9.0/ninja-linux.zip
RUN curl  -L -OJ https://chrome-infra-packages.appspot.com/dl/gn/gn/linux-amd64/+/latest
RUN unzip ninja-linux.zip
RUN unzip gn-linux-amd64.zip
RUN mv ninja /usr/local/bin/
RUN mv gn /usr/local/bin/
RUN rm -rf ninja-linux.zip
RUN rm -rf gn-linux-amd64.zip

ENV LANG zh_CN.UTF-8
ENV LC_ALL zh_CN.UTF-8

#是否默认启用devtoolset-8
#RUN echo 'source scl_source enable devtoolset-8' >> ~/.bashrc

EXPOSE 22
VOLUME [ "/sys/fs/cgroup" ]
CMD ["/usr/sbin/init"]
