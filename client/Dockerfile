FROM node:alpine as builder
WORKDIR '/app'

COPY ./package.json ./

RUN npm install

COPY . .

RUN npm run build
#nginx server inside client would be exposed on 3000 as client is listening on 3000
FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html

