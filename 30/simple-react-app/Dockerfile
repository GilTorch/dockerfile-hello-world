FROM node  AS build_stage

WORKDIR /src/app

COPY package*.json .

RUN npm install 

COPY . .

RUN npm run build 

FROM node:lts-alpine AS production_stage

WORKDIR /src/app

COPY --from=build_stage /src/app/build ./build

RUN npm install -g serve  

EXPOSE 3000 

ENTRYPOINT ["serve", "-s"] 

CMD ["build"]


