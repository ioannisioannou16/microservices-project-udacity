FROM node:12-alpine

WORKDIR /usr/src/app

COPY package*.json /usr/src/app/
COPY src /usr/src/app/src/
COPY tsconfig.json /usr/src/app/

RUN apk --no-cache add --virtual builds-deps build-base python && \
  npm install && \
  npm run tsc && \
  npm prune --production && \
  apk del builds-deps build-base python

ENV NODE_ENV "production"

EXPOSE 8080

CMD ["node", "./www/server.js"]
