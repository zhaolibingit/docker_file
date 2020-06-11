FROM alpine:edge
LABEL maintainer="zhaolibin@sfmail.sf-express.com"
# webproc release settings
ENV WEBPROC_URL https://github.com/jpillora/webproc/releases/download/v0.4.0/webproc_0.4.0_linux_amd64.gz
# fetch dnsmasq and webproc binary
RUN apk update
RUN apk --no-cache add dnsmasq
RUN apk add --no-cache --virtual .build-deps curl
RUN curl -sL $WEBPROC_URL | gzip -d - > /usr/local/bin/webproc
RUN chmod +x /usr/local/bin/webproc
RUN apk del .build-deps
RUN mkdir -p /etc/default/
RUN echo -e "ENABLED=1\nIGNORE_RESOLVCONF=yes" > /etc/default/dnsmasq
COPY dnsmasq.conf /etc/dnsmasq.conf
ADD program.toml /etc/default.toml
#run!
ENTRYPOINT ["webproc","/etc/default.toml"]
