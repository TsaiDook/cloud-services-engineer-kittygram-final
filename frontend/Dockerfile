FROM node:18 as build
WORKDIR /app

COPY package.json package-lock.json ./
RUN npm ci

COPY . .
RUN npm run build

FROM alpine:3.18
WORKDIR /usr/share/nginx/html

COPY --from=build /app/build ./static