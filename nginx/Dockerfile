FROM arm64v8/ubuntu:14.04.5
CMD ["/bin/bash"]
RUN apt-get update && apt-get install -y wget joe && \
    echo "deb http://nginx.org/packages/ubuntu/ trusty nginx" >> /etc/apt/sources.list && \
    echo "deb-src http://nginx.org/packages/ubuntu/ trusty nginx" >> /etc/apt/sources.list && \
    wget http://nginx.org/packages/keys/nginx_signing.key && \
    cat nginx_signing.key | apt-key add - && rm -f nginx_signing.key && \
    apt-key adv --keyserver hkp://pgp.mit.edu:80 --recv-keys 573BFD6B3D8FBC641079A6ABABF5BD827BD9BF62 && \
    apt-get update && \
    apt-get install --no-install-recommends --no-install-suggests -y \
                        ca-certificates \
                        nginx \
                        nginx-module-xslt \
                        nginx-module-geoip \
                        nginx-module-image-filter \
                        nginx-module-perl \
                        nginx-module-njs \
                        gettext-base && \
    rm -rf /var/lib/apt/lists/*
RUN ln -sf /dev/stdout /var/log/nginx/access.log && \
    ln -sf /dev/stderr /var/log/nginx/error.log
EXPOSE 443 80
CMD ["nginx", "-g", "daemon off;"]
