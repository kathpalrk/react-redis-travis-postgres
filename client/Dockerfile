FROM node:alpine as builder
WORKDIR '/app'
##Copy to main working directory like package json into root 
COPY ./package.json ./
RUN npm install
COPY . .
RUN npm run build

FROM nginx
EXPOSE 3000
##Copy from nginx folder which is placed in back folder and copy to Nginx server under conf.d folder#
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
###Production assest build its available under app/build folder which image will take it will take from builder which we have mentioned above.#
COPY --from=builder /app/build /usr/share/nginx/html
