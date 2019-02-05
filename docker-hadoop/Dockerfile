FROM motoskia/centos
MAINTAINER foxutech <prabhakar@foxutech.com>

ADD OpenJDK8U-jdk_x64_linux_hotspot_8u202b08.tar.gz /usr/local/

RUN mv /usr/local/jdk8u202-b08 /usr/local/jdk1.8

ENV JAVA_HOME /usr/local/jdk1.7
ENV PATH $JAVA_HOME/bin:$PATH

RUN yum -y install which && yum clean all

RUN curl -s http://www.eu.apache.org/dist/hadoop/common/hadoop-3.2.0/hadoop-3.2.0.tar.gz | tar -xz -C /usr/local/
RUN cd /usr/local && ln -s ./hadoop-3.2.0 hadoop

ENV HADOOP_HOME /usr/local/hadoop
ENV HADOOP_PREFIX /usr/local/hadoop
ENV HADOOP_COMMON_HOME /usr/local/hadoop
ENV HADOOP_HDFS_HOME /usr/local/hadoop
ENV HADOOP_MAPRED_HOME /usr/local/hadoop
ENV HADOOP_YARN_HOME /usr/local/hadoop
ENV HADOOP_CONF_DIR /usr/local/hadoop/etc/hadoop
ENV YARN_CONF_DIR $HADOOP_PREFIX/etc/hadoop

ENV PATH $HADOOP_HOME/bin:$PATH

RUN ssh-keygen -t rsa -f ~/.ssh/id_rsa -P '' && \
    cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys
