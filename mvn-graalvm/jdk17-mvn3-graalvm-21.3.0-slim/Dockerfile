FROM maven:3-openjdk-17-slim

ENV GRAALVM_VERSION 21.3.0
ENV JAVA_VERSION java17
ENV GRAALVM_HOME /graalvm-ce-$JAVA_VERSION-$GRAALVM_VERSION
ENV PATH $GRAALVM_HOME/bin:$PATH

RUN apt-get update && apt-get install -y wget build-essential libz-dev zlib1g-dev --no-install-recommends \
	&& echo "Downloading GraalVM" \
	&& wget -q https://github.com/graalvm/graalvm-ce-builds/releases/download/vm-$GRAALVM_VERSION/graalvm-ce-$JAVA_VERSION-linux-amd64-$GRAALVM_VERSION.tar.gz \
	&& tar zxf graalvm-ce-$JAVA_VERSION-linux-amd64-$GRAALVM_VERSION.tar.gz \
	&& rm -rf graalvm-ce-$JAVA_VERSION-linux-amd64-$GRAALVM_VERSION.tar.gz \
	&& echo "Installing GraalVM via gu" \
	&& ./graalvm-ce-$JAVA_VERSION-$GRAALVM_VERSION/bin/gu install native-image 
