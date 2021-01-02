FROM node:12-alpine as build
WORKDIR /usr/src/app
COPY package*.json /usr/src/app/
RUN npm install -g ionic
RUN npm install
COPY ./ /usr/src/app/
RUN ionic build --prod

FROM nginx:1.18-alpine
RUN rm -rf /usr/share/nginx/html/*
COPY --from=build /usr/src/app/www/ /usr/share/nginx/html/
COPY ./nginx-custom.conf /etc/nginx/conf.d/default.conf
