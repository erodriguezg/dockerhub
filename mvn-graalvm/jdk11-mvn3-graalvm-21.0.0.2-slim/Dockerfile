FROM maven:3-jdk-11-slim

ENV GRAALVM_VERSION 21.0.0.2
ENV GRAALVM_HOME /graalvm-ce-java11-$GRAALVM_VERSION
ENV PATH $GRAALVM_HOME/bin:$PATH

RUN apt-get update && apt-get install -y wget build-essential libz-dev zlib1g-dev --no-install-recommends \
	&& echo "Downloading GraalVM" \
	&& wget -q https://github.com/graalvm/graalvm-ce-builds/releases/download/vm-$GRAALVM_VERSION/graalvm-ce-java11-linux-amd64-$GRAALVM_VERSION.tar.gz \
	&& tar zxf graalvm-ce-java11-linux-amd64-$GRAALVM_VERSION.tar.gz \
	&& rm -rf graalvm-ce-java11-linux-amd64-$GRAALVM_VERSION.tar.gz \
	&& echo "Installing GraalVM via gu" \
	&& ./graalvm-ce-java11-$GRAALVM_VERSION/bin/gu install native-image 
