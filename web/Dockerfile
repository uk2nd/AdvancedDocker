FROM node:18 AS base
CMD [ "bash" ]

# Build
FROM base AS build
COPY . /workspace
WORKDIR /workspace
# ビルド時に環境変数を受け取るためのARG
ARG REACT_APP_API_SERVER
RUN npm ci && npm run build

# Hosting in nginx
FROM nginx:latest AS production
COPY --from=build /workspace/build /var/www
COPY ./nginx.conf /etc/nginx/conf.d/default.conf
