FROM node:10.14-alpine

RUN mkdir -p /packages
COPY package.json /packages/package.json
COPY yarn.lock /packages/yarn.lock

RUN cd /packages && yarn && \
  mkdir -p /app/viet && ln -s /packages/node_modules /app/viet/node_modules

COPY . /app/viet
WORKDIR /app/viet
ENTRYPOINT node index.js
