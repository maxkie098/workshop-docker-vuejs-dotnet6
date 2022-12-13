FROM node:18-buster-slim as step1
WORKDIR /work
COPY . .
RUN npm install
RUN npm run build

FROM nginx
RUN rm -rf /usr/share/nginx/html/*
COPY --from=step1 /work/dist /usr/share/nginx/html