# Build stage
FROM node:14.11.0-alpine3.10 as build-stage

WORKDIR /app
COPY package*.json ./

RUN npm install

COPY . .

RUN npm run build

# Production stage
FROM nginx:1.18.0-alpine as production-stage
COPY --from=build-stage /app/dist /usr/share/nginx/html
EXPOSE 80
CMD [ "nginx","-g","daemon off;" ]
