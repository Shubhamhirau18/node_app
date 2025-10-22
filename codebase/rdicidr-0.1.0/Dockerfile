## node base image 1st stage
FROM node:15 as builder

WORKDIR /app

COPY package*.json .

RUN npm install

COPY . .

RUN npm run build

## nginx alpine 2nd stage
FROM nginx:alpine

WORKDIR /usr/share/nginx/html

RUN rm -rf ./*

COPY --from=builder /app/build .

EXPOSE 80

ENTRYPOINT ["nginx", "-g", "daemon off;"]