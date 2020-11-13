FROM node:12-alpine as compile-image
RUN apk update && apk add yarn curl bash python g++ make && rm -rf /var/cache/apk/*
RUN curl -sfL https://install.goreleaser.com/github.com/tj/node-prune.sh | bash -s -- -b /usr/local/bin

WORKDIR /usr/src/

COPY package.json ./
RUN yarn install

COPY src/ ./

RUN npm prune --production

RUN /usr/local/bin/node-prune

FROM node:12-alpine

WORKDIR  /usr/src/
COPY --from=compile-image /usr/src/node_modules ./node_modules

COPY --from=compile-image /usr/src/ ./

EXPOSE 80

CMD [ "node", "index.js" ]