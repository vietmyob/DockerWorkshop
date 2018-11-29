FROM node:alpine AS build

RUN mkdir -p /packages
COPY package.json /packages/package.json
COPY yarn.lock /packages/yarn.lock

RUN cd /packages && yarn && \
  mkdir -p /app/viet && ln -s /packages/node_modules /app/viet/node_modules

COPY . /app/viet
WORKDIR /app/viet
RUN yarn build

FROM node:alpine
EXPOSE 5000
RUN yarn global add serve
COPY --from=build /app/viet/build ./build

ENTRYPOINT serve -s build
