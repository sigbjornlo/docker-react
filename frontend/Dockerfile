FROM node:alpine AS build

WORKDIR /app
COPY package.json package-lock.json ./
RUN npm install --quiet
COPY public ./public
COPY src ./src
RUN npm run build

FROM nginx AS production

git EXPOSE 80
COPY --from=build /app/build /usr/share/nginx/html