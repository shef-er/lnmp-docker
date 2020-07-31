FROM nginx:1.17-alpine

ARG USER_ID
ARG GROUP_ID

RUN apk --no-cache add shadow \
    && usermod -u ${USER_ID} nginx \
    && groupmod -g ${GROUP_ID} nginx

EXPOSE 80 443

