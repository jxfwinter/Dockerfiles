FROM centos:7

RUN yum -y install epel-release
RUN yum -y install openssl openssh-server yum-utils

RUN yum -y install unzip kde-l10n-Chinese mlocate vim iproute net-tools bzip2 tcpdump lsof psmisc
RUN yum -y reinstall glibc-common

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

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
