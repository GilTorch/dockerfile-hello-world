FROM node:alpine AS build

WORKDIR /src/app

COPY package*.json .

RUN npm ci 

COPY . . 

RUN npm run build 

FROM nginx:alpine-slim AS production 

COPY --from=build /src/app/build /var/www/website

COPY nginx.conf /etc/nginx/nginx.conf 

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]


