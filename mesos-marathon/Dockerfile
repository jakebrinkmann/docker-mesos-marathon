# Marathon Dockerfile
FROM ubuntu:14.04
MAINTAINER Mesosphere <support@mesosphere.io>

## DEPENDENCIES ##
RUN echo "deb http://repos.mesosphere.io/ubuntu/ trusty main" > /etc/apt/sources.list.d/mesosphere.list
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv E56151BF
RUN apt-get update
RUN apt-get install --assume-yes mesos python-software-properties curl 
RUN apt-get install --assume-yes software-properties-common
RUN add-apt-repository ppa:openjdk-r/ppa && apt-get update && apt-get install --assume-yes openjdk-8-jdk && \
	update-alternatives --config java
#ENV JAVA_HOME /usr/lib/jvm/openjdk-8
ENV JAVA_HOME /usr/lib/jvm/java-8-openjdk-amd64

## MARATHON ##
RUN  curl https://downloads.mesosphere.com/marathon/releases/1.5.2/marathon-1.5.2.tgz | tar -xzf - -C /opt && \
	mv /opt/marathon-1.5.2 /opt/marathon

EXPOSE 8080
WORKDIR /opt/marathon
#CMD ["--help"]
ENTRYPOINT ["/opt/marathon/bin/marathon"]
