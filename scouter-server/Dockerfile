FROM frolvlad/alpine-oraclejdk8
MAINTAINER marjoram1984

EXPOSE 6100

ADD supervisord.conf /etc/conf/supervisord.conf

RUN apk add --no-cache bash gawk sed grep bc coreutils
RUN mkdir opt \
 && wget -q -O /opt/scouter-all-1.9.0.tar.gz https://github.com/scouter-project/scouter/releases/download/v1.9.0/scouter-all-1.9.0.tar.gz \
 && cd /opt \
 && tar xvf scouter-all-1.9.0.tar.gz

RUN apk add --update supervisor && rm -rf /tmp/* /var/cache/apk/*

ENV LANG=ko_KR.utf8 TZ=Asia/Seoul

ENTRYPOINT ["supervisord", "--nodaemon", "--configuration", "/etc/conf/supervisord.conf"]



