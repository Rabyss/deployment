FROM ubuntu:16.04

LABEL version 1.0
LABEL description "Base scala image for reminisceme"

RUN echo debconf shared/accepted-oracle-license-v1-1 select true | debconf-set-selections
RUN echo debconf shared/accepted-oracle-license-v1-1 seen true | debconf-set-selections
RUN apt-get -qq update && apt-get -qq -y install apt-transport-https software-properties-common
RUN echo "deb https://dl.bintray.com/sbt/debian /" | tee -a /etc/apt/sources.list.d/sbt.list
RUN apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 642AC823
RUN add-apt-repository ppa:webupd8team/java
RUN apt-get -qq update
RUN apt-get -qq install -y oracle-java8-installer sbt git
COPY bootstrap bootstrap
RUN cd bootstrap && sbt run
RUN rm -rf bootstrap
