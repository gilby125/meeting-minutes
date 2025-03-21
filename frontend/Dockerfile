FROM node:20-alpine

WORKDIR /app

COPY package*.json ./

RUN npm cache clean --force && npm install

COPY . .

RUN npm install next -g
ENV PATH="/root/node_modules/.bin:${PATH}"
CMD ["npm", "run", "dev"]
