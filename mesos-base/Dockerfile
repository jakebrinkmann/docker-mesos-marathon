FROM centos:7

WORKDIR /opt

## Install dependencies
RUN yum install -y epel-release && \
	yum groupinstall -y "Development Tools" && \
	curl -L http://repos.fedorapeople.org/repos/dchen/apache-maven/epel-apache-maven.repo > /etc/yum.repos.d/epel-apache-maven.repo && \
	yum install -y apache-maven python-devel python-six python-virtualenv java-1.8.0-openjdk-devel zlib-devel libcurl-devel openssl-devel cyrus-sasl-devel cyrus-sasl-md5 apr-devel subversion-devel apr-util-devel
ENV JAVA_HOME="/usr/lib/jvm/java-1.8.0/"
ENV PATH="${PATH}:${JAVA_HOME}/bin"

## Install Mesos 1.3.0
ENV MESOS_VER="1.3.0"
ENV MESOS_HOME="/usr/local/mesos"
RUN groupadd mesos
RUN useradd -d /home/mesos -g mesos -m mesos
RUN curl -L "http://www.apache.org/dist/mesos/$MESOS_VER/mesos-$MESOS_VER.tar.gz" \
	 | tar zx && mv "mesos-$MESOS_VER" $MESOS_HOME && \
	mkdir -p "${MESOS_HOME}/build" && \
	chown -R mesos:mesos $MESOS_HOME
ENV PATH="${PATH}:$MESOS_HOME/bin"

## Build Mesos
USER mesos
WORKDIR /usr/local/mesos/build
RUN ../configure -q
RUN make -j $(nproc) V=0
RUN make check
RUN make install

WORKDIR /var/lib/mesos
EXPOSE 5050

