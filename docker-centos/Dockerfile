FROM centos
MAINTAINER foxutech <prabhakar@foxutech.com>

RUN echo 'root:!23$QweR' | chpasswd

RUN rpm --import /etc/pki/rpm-gpg/RPM*

RUN \
    yum -y install \
        openssh openssh-server openssh-clients \
        sudo passwd wget &&\
        yum clean all

RUN sshd-keygen
RUN sed -i "s/#UsePrivilegeSeparation.*/UsePrivilegeSeparation no/g" /etc/ssh/sshd_config
RUN sed -i "s/UsePAM.*/UsePAM no/g" /etc/ssh/sshd_config

RUN mkdir /var/run/sshd
EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
