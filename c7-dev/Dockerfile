FROM centos:7

RUN yum -y install epel-release
RUN yum -y install https://download.postgresql.org/pub/repos/yum/reporpms/EL-7-x86_64/pgdg-redhat-repo-latest.noarch.rpm
RUN yum -y install centos-release-scl
RUN yum -y install openssl openssh-server yum-utils

RUN yum -y install diffutils git unzip kde-l10n-Chinese make automake autoconf openssl-devel libcurl-devel zlib-devel python-devel mlocate patch vim iproute net-tools bzip2 cifs-utils tcpdump lsof psmisc
RUN yum -y install scl-utils devtoolset-9
RUN yum -y install gcc-c++ gdb
RUN yum -y reinstall glibc-common
RUN yum -y install ninja-build


RUN curl -L -OJ https://github.com/Kitware/CMake/releases/download/v3.19.1/cmake-3.19.1-Linux-x86_64.sh
RUN sh cmake-3.19.1-Linux-x86_64.sh --prefix=/usr/local --exclude-subdir --skip-license
RUN rm -rf cmake-3.19.1-Linux-x86_64.sh

RUN curl -L -OJ https://chrome-infra-packages.appspot.com/dl/gn/gn/linux-amd64/+/_mqsWgUKYXT-P_QYuuG1J5vH3Vzd6u-Lo5giO0XDmLoC
RUN unzip gn-linux-amd64.zip
RUN mv gn /usr/local/bin/
RUN rm -rf gn-linux-amd64.zip
RUN ln -s /usr/bin/ninja-build /usr/local/bin/ninja


RUN yum clean all
RUN localedef -c -f UTF-8 -i zh_CN zh_CN.utf8
RUN export LANG=zh_CN.UTF-8
RUN echo 'LANG="zh_CN.UTF-8"' > /etc/locale.conf
RUN echo "export LANG=zh_CN.UTF-8" >> /etc/profile
RUN echo 'rt20dev88' | passwd --stdin root
RUN ssh-keygen -A
RUN sed -i -r 's/^(.*pam_nologin.so)/#\1/' /etc/pam.d/sshd

ENV LANG zh_CN.UTF-8
ENV LC_ALL zh_CN.UTF-8

#是否默认启用devtoolset-8
#RUN echo 'source scl_source enable devtoolset-8' >> ~/.bashrc

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
