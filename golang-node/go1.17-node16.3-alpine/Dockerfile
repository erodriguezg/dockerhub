FROM golang:1.17-alpine3.15

ENV NODE_VERSION 16.13.2-r0
ENV NPM_VERSION 8.1.3-r0

RUN apk update \
	&& apk --no-cache add alpine-sdk nodejs=$NODE_VERSION npm=$NPM_VERSION   

