#Docker flie for frontend
FROM node:18 AS build

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

RUN npx ng build --prod

FROM nginx:alpine

COPY --from=build /app/dist/crud-dd-task-mean-app /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]