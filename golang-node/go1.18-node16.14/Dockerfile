FROM golang:1.18

ENV NODE_VERSION v16.14.2
ENV NODE_DISTRO linux-x64

ENV PATH /usr/local/lib/nodejs/node-$NODE_VERSION-$NODE_DISTRO/bin:$PATH

RUN apt update \
	&& apt install xz-utils \
	&& mkdir -p /usr/local/lib/nodejs \
	&& curl https://nodejs.org/dist/$NODE_VERSION/node-$NODE_VERSION-$NODE_DISTRO.tar.xz -o node.tar.xz \
	&& tar -xJvf node.tar.xz -C /usr/local/lib/nodejs \
	&& rm node.tar.xz 

