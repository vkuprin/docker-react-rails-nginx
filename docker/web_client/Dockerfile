FROM node:latest

# Setting working directory. All the path will be relative to WORKDIR
WORKDIR /usr/src/app

RUN npm install yarn -g

# Installing dependencies
COPY client/package*.json ./
RUN yarn install

# Copying source files
COPY client .

# Building app
RUN yarn build

RUN cp .next/service-worker.js public

# Running the app
CMD [ "yarn", "start" ]