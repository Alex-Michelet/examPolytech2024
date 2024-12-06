FROM node:10-alpine as front_builder

WORKDIR /app

COPY . .

RUN npm install -y

RUN npm run build

# prepare image to serve web app

FROM nginx:1.27-alpine

# copy from front builder
COPY --from=front_builder /app/dist /usr/share/nginx/html

COPY nginx/ /etc/nginx/

LABEL maintenair="alex"

COPY entrypoint.sh /docker-entrypoint.d/entrypoint.sh
