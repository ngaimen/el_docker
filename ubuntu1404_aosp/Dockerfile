#
# Minimum Docker image to build Android AOSP
#
FROM ubuntu:14.04
ADD openjdk-8-jdk_8u45-b14-1_amd64.deb /home/
ADD openjdk-8-jre_8u45-b14-1_amd64.deb /home/
ADD openjdk-8-jre-headless_8u45-b14-1_amd64.deb /home/

MAINTAINER Evan Lo <evan_lo@126.com>

# /bin/sh points to Dash by default, reconfigure to use bash until Android
# build becomes POSIX compliant
RUN echo "dash dash/sh boolean false" | debconf-set-selections && \
    dpkg-reconfigure -p critical dash

RUN apt-get update && \
    apt-get install -y ca-certificates-java java-common libcups2 liblcms2-2 libjpeg8 libnss3 libfreetype6  \
        libpcsclite1 libx11-6 libxext6 libxi6 libxrender1 libxtst6 libgtk2.0-0 libxrandr2 libxinerama1 libgl1-mesa-glx \
        libatk-wrapper-java-jni libasound2 libgif4
RUN dpkg -i /home/openjdk-8-jre-headless_8u45-b14-1_amd64.deb
RUN dpkg -i /home/openjdk-8-jre_8u45-b14-1_amd64.deb
RUN dpkg -i /home/openjdk-8-jdk_8u45-b14-1_amd64.deb
RUN apt-get -f install

RUN rm /home/openjdk*

RUN apt-get install -y bc bison bsdmainutils build-essential curl \
        flex g++-multilib gcc-multilib git gnupg gperf lib32ncurses5-dev \
        lib32z1-dev libesd0-dev libncurses5-dev \
        libsdl1.2-dev libwxgtk3.0-dev libxml2-utils lzop sudo \
        pngcrush schedtool xsltproc zip zlib1g-dev graphviz && \
    apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

ADD repo /usr/local/bin/
RUN chmod 755 /usr/local/bin/*

ENV USER root

