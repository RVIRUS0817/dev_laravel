FROM nginx:1.25.2-alpine

# Setup UTC+9
RUN apk --update add tzdata && \
    cp /usr/share/zoneinfo/Asia/Tokyo /etc/localtime && \
    apk del tzdata && \
    rm -rf /var/cache/apk/*

# install packages
RUN apk update && \
    apk upgrade && \
    apk add --update --no-cache \
    bash \
    nginx \
    sudo \
    supervisor \
    tzdata \
    vim

## nginx
COPY conf/nginx.conf /etc/nginx/nginx.conf
COPY conf/dev.adachin.com.conf /etc/nginx/conf.d/dev.adachin.com.conf

# setting superviser
COPY supervisor/supervisord.conf /etc/supervisord.conf
COPY supervisor/nginx.conf /etc/supervisor/conf.d/nginx.conf
RUN echo files = /etc/supervisor/conf.d/*.conf >> /etc/supervisord.conf

EXPOSE 80
#CMD ["/usr/bin/supervisord"]
CMD ["supervisord", "-c", "/etc/supervisord.conf"]
