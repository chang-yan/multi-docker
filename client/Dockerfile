FROM node:16-alpine as builder

WORKDIR /app
COPY . .

RUN npm install
RUN npm run build

FROM nginx:1.21.3-alpine
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html
