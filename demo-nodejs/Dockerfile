FROM node:18-buster-slim
WORKDIR /demo
COPY package.json package.json
RUN npm install
COPY . .
CMD ["node", "server.js"]