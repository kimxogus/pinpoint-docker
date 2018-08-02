FROM tomcat:8-jre8-alpine

LABEL maintainer="Roy Kim <roy.kim@navercorp.com>"

ARG PINPOINT_VERSION=${PINPOINT_VERSION:-1.7.3}
ARG INSTALL_URL=https://github.com/naver/pinpoint/releases/download/${PINPOINT_VERSION}/pinpoint-web-${PINPOINT_VERSION}.war

COPY /build/scripts/start-web.sh /usr/local/bin/

RUN apk add --no-cache bash \
    && apk add --virtual=build-deps curl \
    && chmod a+x /usr/local/bin/start-web.sh \
    && curl -SL ${INSTALL_URL} -o pinpoint-web.war \
    && rm -rf /usr/local/tomcat/webapps \
    && mkdir -p /usr/local/tomcat/webapps/ROOT \
    && unzip pinpoint-web.war -d /usr/local/tomcat/webapps/ROOT \
    && rm -rf pinpoint-web.war \
    && apk del build-deps

ENTRYPOINT ["/usr/local/bin/start-web.sh"]
