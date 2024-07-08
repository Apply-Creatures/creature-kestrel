ARG APP_PATH=/opt/outline
FROM outlinewiki/outline-base as base

ARG APP_PATH
WORKDIR $APP_PATH

# ---
FROM node:20-slim AS runner

LABEL org.opencontainers.image.source="https://github.com/outline/outline"

ARG APP_PATH
WORKDIR $APP_PATH
ENV NODE_ENV production

COPY --from=base $APP_PATH/build ./build
COPY --from=base $APP_PATH/server ./server
COPY --from=base $APP_PATH/public ./public
COPY --from=base $APP_PATH/.sequelizerc ./.sequelizerc
COPY --from=base $APP_PATH/node_modules ./node_modules
COPY --from=base $APP_PATH/package.json ./package.json

# install redis and email server
RUN apt-get update && apt-get install -y redis-server postfix

RUN touch /etc/postfix/password

COPY main.cf /etc/postfix/main.cf


# Set mail environment variables
ENV SMTP_HOST=tracker.applycreatures.com
ENV SMTP_PORT=25
ENV SMTP_USERNAME=
ENV SMTP_PASSWORD=
ENV SMTP_FROM_EMAIL=from@tracker.applycreatures.com
ENV SMTP_REPLY_EMAIL=no-reply@tracker.applycreatures.com
ENV SMTP_SECURE=false

## Install bun
RUN curl -fsSL https://bun.sh/install | bash

RUN mkdir -p /opt/outline && chmod -R 777 /opt/outline

# Create a non-root user compatible with Debian
RUN addgroup --gid 1001 nodejs && \
  adduser --uid 1001 --ingroup nodejs nodejs && \
  chown -R nodejs:nodejs $APP_PATH/build && \
  mkdir -p /var/lib/outline && \
	chown -R nodejs:nodejs /var/lib/outline

ENV FILE_STORAGE_LOCAL_ROOT_DIR /var/lib/outline/data
RUN mkdir -p "$FILE_STORAGE_LOCAL_ROOT_DIR" && \
  chown -R nodejs:nodejs "$FILE_STORAGE_LOCAL_ROOT_DIR" && \
  chmod 1777 "$FILE_STORAGE_LOCAL_ROOT_DIR"

VOLUME /var/lib/outline/data

EXPOSE 3000

CMD ["sh", "-c", "/usr/sbin/postfix start & redis-server & yarn start"]
