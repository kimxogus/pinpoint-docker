FROM tomcat:8-jre8-alpine

LABEL maintainer="Roy Kim <roy.kim@navercorp.com>"

COPY /build/pinpoint-quickstart-testapp.war quickstart.war

RUN apk add --no-cache bash \
    && rm -rf /usr/local/tomcat/webapps \
    && mkdir -p /usr/local/tomcat/webapps/ROOT \
    && unzip quickstart.war -d /usr/local/tomcat/webapps/ROOT \
    && rm -rf quickstart.war

CMD [ "catalina.sh", "run" ]
