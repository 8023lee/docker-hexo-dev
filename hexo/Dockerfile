# FROM node:8.15-alpine
FROM alpine:3.8
# --- 创建和主机登录用户相同 uid/gid 的用户 ---

ARG X_GID
ARG X_UID

RUN set -eux; \
    if [ -z "`getent group ${X_GID}`" ]; then \
        addgroup --system --gid ${X_GID} xu; \
    fi; \
    adduser --system --disabled-password -u ${X_UID} -g `getent group ${X_GID} | cut -d: -f3` xu

WORKDIR /code
