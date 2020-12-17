FROM ubuntu:latest

ENV K8S_VERSION 1.19.5

RUN apt-get update \
	&& apt-get install wget vim -y

RUN cd /root \
	&& wget https://storage.googleapis.com/kubernetes-release/release/v$K8S_VERSION/bin/linux/amd64/kubectl \
	&& chmod +x kubectl \
	&& mv kubectl /usr/local/bin \
