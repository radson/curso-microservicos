FROM nginx:1.15.0-alpine
RUN rm /etc/nginx/conf.d/default.conf
#RUN apk add --no-cache bash
#COPY ./nginx.conf /etc/nginx/conf.d

ENV DOCKERIZE_VERSION v0.6.1
RUN wget https://github.com/jwilder/dockerize/releases/download/$DOCKERIZE_VERSION/dockerize-alpine-linux-amd64-$DOCKERIZE_VERSION.tar.gz \
    && tar -C /usr/local/bin -xzvf dockerize-alpine-linux-amd64-$DOCKERIZE_VERSION.tar.gz \
    && rm dockerize-alpine-linux-amd64-$DOCKERIZE_VERSION.tar.gz


RUN echo "daemon off;" >> /etc/nginx/nginx.conf

ADD nginx.tmpl /etc/nginx/conf.d/nginx.tmpl

CMD ["dockerize", "-template", "/etc/nginx/conf.d/nginx.tmpl:/etc/nginx/conf.d/default.conf", "nginx"]
