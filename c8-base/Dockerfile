FROM centos:8

RUN dnf -y install openssl openssh-server dnf-utils
RUN dnf -y install mlocate vim iproute net-tools bzip2 passwd python36 tcpdump unzip lsof psmisc
RUN dnf -y install glibc-locale-source glibc-langpack-zh

RUN dnf clean all

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
