FROM node:8.14.0-jessie

WORKDIR /project

COPY ./docker-config/buildchain/package.json package.json

RUN cd /project && yarn install

CMD yarn run build
