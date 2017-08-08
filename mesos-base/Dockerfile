FROM centos:7

WORKDIR /opt

## Install dependencies
RUN yum install -y epel-release && \
	yum groupinstall -y "Development Tools" && \
	curl -L http://repos.fedorapeople.org/repos/dchen/apache-maven/epel-apache-maven.repo > /etc/yum.repos.d/epel-apache-maven.repo && \
	yum install -y apache-maven python-devel python-six python-virtualenv java-1.8.0-openjdk-devel zlib-devel libcurl-devel openssl-devel cyrus-sasl-devel cyrus-sasl-md5 apr-devel subversion-devel apr-util-devel

## Install Mesos 1.3.0
ENV MESOS_VER="1.3.0"
ENV MESOS_HOME="/usr/local/mesos"
RUN groupadd mesos
RUN useradd -d /home/mesos -g mesos -m mesos
RUN curl -L "http://www.apache.org/dist/mesos/$MESOS_VER/mesos-$MESOS_VER.tar.gz" \
	 | tar zx && mv "mesos-$MESOS_VER" $MESOS_HOME && \
	chown -R mesos:mesos $MESOS_HOME
ENV PATH="${PATH}:$MESOS_HOME/bin"

## Install JAVA JDK 1.8.0
ENV JAVA_HOME "/usr/local/java"
RUN curl -L -H "Cookie: oraclelicense=accept-securebackup-cookie" \
	http://download.oracle.com/otn-pub/java/jdk/8u131-b11/d54c1d3a095b4ff2b6607d096fa80163/jdk-8u131-linux-x64.tar.gz | tar zx && \
	mv jdk1.8.0_131 $JAVA_HOME
ENV PATH="${PATH}:${JAVA_HOME}/bin"

## Build Mesos
USER mesos
RUN mkdir -p "${MESOS_HOME}/build"
RUN cd "${MESOS_HOME}/build"
RUN ../configure -q
RUN make -j $(nproc) V=0
RUN make check
RUN make install

WORKDIR /var/lib/mesos
EXPOSE 5050

