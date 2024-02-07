# FROM node:18

# RUN apt-get update && apt-get install -y wget

# ENV  DOCKERIZE_VERSION=v0.6.1

# RUN wget https://github.com/jwilder/dockerize/releases/download/$DOCKERIZE_VERSION/dockerize-linux-amd64-$DOCKERIZE_VERSION.tar.gz   && tar -C /usr/local/bin -xzvf dockerize-linux-amd64-$DOCKERIZE_VERSION.tar.gz   && rm dockerize-linux-amd64-$DOCKERIZE_VERSION.tar.gz

# USER node

# WORKDIR /usr/src/app

FROM node:current-alpine3.18 as builder

WORKDIR /usr/src/app
COPY package.json .
RUN npm install
COPY . .

RUN apk add --no-cache curl

ENV DOCKERIZE_VERSION v0.19.0
RUN curl -sfL \
  https://github.com/powerman/dockerize/releases/download/${DOCKERIZE_VERSION}/dockerize-$(uname -s)-$(uname -m) | \
  install /dev/stdin /usr/local/bin/dockerize
