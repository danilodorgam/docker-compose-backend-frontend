FROM node:14.15.5 AS build
MAINTAINER dhdorgam
RUN mkdir /app-site
WORKDIR /app-site
COPY projeto /app-site
RUN npm install
RUN  npm run build
#
# Package stage
#
FROM nginx:latest
COPY --from=build /app-site/dist/ /usr/share/nginx/html
COPY nginx/default.conf /etc/nginx/conf.d/default.conf