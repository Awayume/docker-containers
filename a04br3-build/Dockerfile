# Base is: https://android.googlesource.com/platform/build/+/master/tools/docker/Dockerfile
FROM ubuntu:14.04
MAINTAINER Awayume <git@awayume.jp>
RUN apt-get update && apt-get install -y git-core gnupg flex bison gperf build-essential zip curl zlib1g-dev gcc-multilib g++-multilib libc6-dev-i386 lib32ncurses5-dev x11proto-core-dev libx11-dev lib32z-dev ccache libgl1-mesa-dev libxml2-utils xsltproc unzip python python3 openjdk-7-jdk bc
RUN curl -o jdk8.tgz https://android.googlesource.com/platform/prebuilts/jdk/jdk8/+archive/master.tar.gz \
 && tar -zxf jdk8.tgz linux-x86 \
 && mv linux-x86 /usr/lib/jvm/java-8-openjdk-amd64 \
 && rm -rf jdk8.tgz
RUN curl -o /usr/local/bin/repo https://storage.googleapis.com/git-repo-downloads/repo \
 && sed -i '1s/python/python3/' /usr/local/bin/repo \
 && chmod a+x /usr/local/bin/repo
RUN curl -o android-gcc.tgz https://android.googlesource.com/platform/prebuilts/gcc/linux-x86/aarch64/aarch64-linux-android-4.9/+archive/0d0a573f4295719e0dacf298be83bd48e9a9bb6d.tar.gz \
 && mkdir -p /opt/android-gcc \
 && tar -zxf android-gcc.tgz -C /opt/android-gcc \
 && chmod a+x /opt/android-gcc/bin/* \
 && rm android-gcc.tgz
ENV PATH /opt/android-gcc/bin:/opt/android-gcc/aarch64-linux-android:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games
ENV ARCH arm64
ENV CROSS_COMPILE aarch64-linux-android-
