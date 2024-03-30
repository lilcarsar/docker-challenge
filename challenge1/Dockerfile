FROM nginx:latest
WORKDIR /app
COPY public/index.html /usr/share/nginx/html/index.html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]