FROM node:18 as base



# Build

FROM base as build
COPY . /workspace
WORKDIR /workspace
ARG REACT_APP_API_SERVER
RUN npm ci && npm run build


# hosting in nginx

FROM nginx:latest AS producion
COPY --from=build /workspace/build /var/www
COPY nginx.conf /etc/nginx/conf.d/default.conf



CMD [ "bash" ]