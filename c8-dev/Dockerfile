FROM centos:8

RUN dnf -y install openssl openssh-server dnf-utils
RUN yum-config-manager --enable PowerTools
RUN dnf -y install https://download.postgresql.org/pub/repos/yum/reporpms/EL-8-x86_64/pgdg-redhat-repo-latest.noarch.rpm
RUN dnf -qy module disable postgresql
RUN dnf -y install mlocate patch vim iproute net-tools bzip2 passwd postgresql12 python36 tcpdump unzip lsof psmisc
RUN dnf -y install glibc-locale-source glibc-langpack-zh

RUN dnf -y install openssl-devel libcurl-devel zlib-devel pcre-devel postgresql12-devel python36-devel
RUN dnf -y install git gcc-c++ gdb make automake autoconf cifs-utils diffutils

RUN yum-config-manager --add-repo http://www.nasm.us/nasm.repo
RUN dnf -y install nasm ninja-build

RUN dnf clean all

RUN curl  -L -OJ https://chrome-infra-packages.appspot.com/dl/gn/gn/linux-amd64/+/latest
RUN curl -L -OJ https://github.com/Kitware/CMake/releases/download/v3.16.5/cmake-3.16.5-Linux-x86_64.sh
RUN sh cmake-3.16.5-Linux-x86_64.sh --prefix=/usr/local --exclude-subdir --skip-license
RUN unzip gn-linux-amd64.zip
RUN ln -s /usr/bin/ninja-build /usr/local/bin/ninja
RUN mv gn /usr/local/bin/
RUN rm -rf gn-linux-amd64.zip
RUN rm -rf cmake-3.16.5-Linux-x86_64.sh

RUN sed -i "/mv -i/a\alias ls='ls --color'" /root/.bashrc
RUN localedef -c -f UTF-8 -i zh_CN zh_CN.utf8;\
export LANG=zh_CN.UTF-8;\
echo 'LANG="zh_CN.UTF-8"' > /etc/locale.conf;\
echo "export LANG=zh_CN.UTF-8" >> /etc/profile;

RUN echo 'rt20dev88' | passwd --stdin root;\
ssh-keygen -A;\
sed -i -r 's/^(.*pam_nologin.so)/#\1/' /etc/pam.d/sshd;

ENV LANG zh_CN.UTF-8
ENV LC_ALL zh_CN.UTF-8

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
