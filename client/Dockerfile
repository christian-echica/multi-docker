FROM node:alpine as builder
WORKDIR '/app'
COPY ./package.json ./
RUN npm install
RUN npm update -g
RUN npm install -g yarn
RUN npm audit fix
RUN npm fund
RUN yarn remove jest-dom
RUN yarn add -D @testing-library/jest-dom
COPY . .
RUN npm run build

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html