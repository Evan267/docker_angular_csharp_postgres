# Build stage
FROM node:20.16.0-alpine3.19 AS build
WORKDIR /app
COPY ./src/ ./
RUN npm ci
RUN npm run build


# Final stage
FROM nginx:alpine
COPY nginx/nginx.conf /etc/nginx/nginx.conf
COPY --from=build /app/dist/src/browser /usr/share/nginx/html
EXPOSE 80
ENTRYPOINT ["nginx", "-g", "daemon off;"]