FROM node:12-alpine

WORKDIR /usr/src/app

COPY package*.json /usr/src/app/
COPY src /usr/src/app/src/
COPY tsconfig.json /usr/src/app/

RUN npm install && \
  npm run tsc && \
  npm prune --production

ENV NODE_ENV "production"

EXPOSE 8080

CMD ["node", "./www/server.js"]
