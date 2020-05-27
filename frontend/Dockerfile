FROM node:alpine

WORKDIR /app
COPY package.json package-lock.json ./
RUN npm install --quiet
COPY public ./public
COPY src ./src
RUN npm run build

FROM nginx AS production

EXPOSE 80
COPY --from=0 /app/build /usr/share/nginx/html