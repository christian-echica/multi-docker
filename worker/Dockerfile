FROM node:alpine
WORKDIR "/app"
COPY ./package.json ./
RUN npm install
RUN npm update -g
RUN yarn remove jest-dom
RUN yarn add -D @testing-library/jest-dom
COPY . .
CMD ["npm", "run", "start"]