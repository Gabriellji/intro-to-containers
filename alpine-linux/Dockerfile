
# build stage
FROM node:12-stretch AS build

WORKDIR /build

COPY package-lock.json package.json ./

RUN npm ci

COPY . .


# runtime stage
FROM alpine:3.10

RUN apk add --update nodejs

RUN addgroup -S node && adduser -S node -G node

USER node

RUN mkdir /home/node/code

WORKDIR /home/node/code

COPY --from=build --chown=node:node /build .

CMD ["node", "index.js"]






#FROM alpine:3.10

#RUN apk add --update nodejs npm

#RUN addgroup -S node && adduser -S node -G node

#USER node

#RUN mkdir /home/node/code

#WORKDIR /home/node/code

#COPY --chown=node:node package-lock.json package.json ./

#RUN npm ci

#COPY --chown=node:node . .

#CMD ["node", "index.js"]










#USER node

#RUN mkdir /home/node/code

#WORKDIR /home/node/code

#COPY --chown=node:node package-lock.json package.json ./

#RUN npm ci

#COPY --chown=node:node . .

#EXPOSE 3000

#CMD ["node", "index.js"]