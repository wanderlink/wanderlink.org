FROM node:12-buster

WORKDIR /usr/src/wanderlink.org

COPY package*.json ./
RUN npm install

COPY . .

CMD [ "npm", "run", "start:prod" ]
