FROM nginx:1.14.2-alpine

ARG DOMAIN

COPY ./nginx/conf.d/ /etc/nginx/conf.d/

RUN envsubst '${DOMAIN}' < /etc/nginx/conf.d/sites.conf > /etc/nginx/conf.d/default.conf
