FROM node:18 as build

WORKDIR /app
COPY ./my-app ./

RUN rm -rf node_modules package-lock.json

RUN npm install

# Сборка проекта
RUN npm run build

FROM nginx:alpine

COPY --from=build /app/dist /usr/share/nginx/html
COPY ./nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
