FROM node:16-alpine as builder
WORKDIR '/app'
COPY ./package.json ./
RUN npm install -g npm@8.19.2
RUN npm install
COPY . .
RUN npm run build


FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf ./nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html