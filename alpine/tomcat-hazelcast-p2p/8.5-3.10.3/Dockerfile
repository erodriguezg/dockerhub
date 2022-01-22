FROM erodriguezg/oracle-jdk-alpine:8u181

ENV CATALINA_HOME /opt/tomcat
ENV PATH $CATALINA_HOME/bin:$PATH
ENV TOMCAT_DOWNLOAD_URL http://www-eu.apache.org/dist/tomcat/tomcat-8/v8.5.32/bin/apache-tomcat-8.5.32.tar.gz

RUN apk add --no-cache --virtual=build-dependencies wget && \
  wget -O /tmp/tomcat.tar.gz $TOMCAT_DOWNLOAD_URL && \
  cd /tmp && tar -xzf /tmp/tomcat.tar.gz && mkdir -p $CATALINA_HOME && mv apache-tomcat-*/* $CATALINA_HOME && rm -rf /tmp/* && \
  apk del build-dependencies

COPY hazelcast-all-3.10.3.jar hazelcast-tomcat85-sessionmanager-1.1.3.jar hazelcast.xml $CATALINA_HOME/lib/
COPY context.xml server.xml $CATALINA_HOME/conf/

EXPOSE 8080
CMD ["catalina.sh", "run"]