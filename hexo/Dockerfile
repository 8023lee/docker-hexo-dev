FROM node:8.15-alpine

# --- 创建和主机登录用户相同 uid/gid 的用户 ---

ARG X_GID
ARG X_UID

RUN set -eux; \
    if [ -z "`getent group ${X_GID}`" ]; then \
        addgroup --system --gid ${X_GID} xu; \
    fi; \
    adduser --system --disabled-password -u ${X_UID} -g ${X_GID} xu

RUN su - xu && \
	mkdir /home/xu/.npm-global && \
	npm config set prefix '/home/xu/.npm-global' && \
	export PATH=/home/xu/.npm-global/bin:$PATH && \
	source /home/xu/.profile

RUN chown -R xu:$X_GID /usr/local/lib/node_modules

WORKDIR /code
