FROM node:14.15.3-alpine as node
RUN mkdir -p /app
WORKDIR /app
COPY package.json /app/
RUN npm install install -f
COPY . /app/
RUN npm run build --prod
# stage 2
FROM nginx:alpine
COPY --from=node /app/dist/* /usr/share/nginx/html
ENV BASEURL = http://192.168.124.197
ENV PORT = 8089
CMD [ "nginx","-g","daemon off;" ]
EXPOSE 80