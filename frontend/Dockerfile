FROM node:12-alpine AS build

WORKDIR /frontend
COPY . .

RUN npm i
RUN npm run-script build

FROM nginx

COPY --from=build /frontend/build /var/www/html
COPY default.conf /etc/nginx/conf.d/default.conf

EXPOSE 80

CMD ["nginx","-g","daemon off;"]