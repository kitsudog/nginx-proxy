FROM nginxproxy/nginx-proxy:1.3.1-alpine
RUN mkdir -p /etc/nginx/vhost.d
RUN { \
      echo 'gzip on;'; \
    } > /etc/nginx/conf.d/my_proxy.conf
RUN { \
      echo 'proxy_connect_timeout 3s;';\
      echo 'proxy_timeout 300s;';\
      echo 'client_max_body_size 100m;'; \
    } > /etc/nginx/vhost.d/default_location
ENV LOG_FORMAT='$host "[$http_x_forwarded_for Proxy-pass=$upstream_addr]" $remote_addr $remote_user [$time_local] "$request" $status $body_bytes_sent "$http_referer" "$http_user_agent"' \
    RESOLVERS=8.8.8.8 \
    HTTPS_METHOD=noredirect \
    HSTS="max-age=31536000; includeSubDomains; preload" \
    HTTP_PORT=80 \
    HTTPS_PORT=443 \
    TRUST_DOWNSTREAM_PROXY=true \
    DEFAULT_ROOT=503 \
    SHA1_UPSTREAM_NAME=false \
    #DISABLE_ACCESS_LOGS= \
    SSL_POLICY='Mozilla-Intermediate' \
    ENABLE_IPV6=false \
    TZ=Asia/Shanghai

