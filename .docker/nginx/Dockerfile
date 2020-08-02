FROM nginx:1.17-alpine

MAINTAINER Ernest Shefer <shef-er@ya.ru>

ADD nginx.conf  /etc/nginx/nginx.conf
#ADD conf.d/     /etc/nginx/conf.d/
ADD snippets/   /etc/nginx/snippets/

#ARG USER_ID
#ARG GROUP_ID
#
#RUN apk --no-cache add shadow \
#    && usermod -u ${USER_ID} nginx \
#    && groupmod -g ${GROUP_ID} nginx
#
#USER "${USER_ID}:${GROUP_ID}"


