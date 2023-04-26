FROM node:alpine as builder

WORKDIR /app

COPY ./package*.json ./

RUN npm install

COPY . .

RUN npm run build

# Second phase

FROM nginx

EXPOSE 3000

COPY ./nginx/default.conf /etcnginx/conf.d/default.conf

COPY --from=0 /app/build /usr/share/nginx/html
