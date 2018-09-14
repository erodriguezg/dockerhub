FROM erodriguezg/oracle-jdk-alpine:8u181

ENV CATALINA_HOME /opt/tomcat
ENV PATH $CATALINA_HOME/bin:$PATH
ENV TOMCAT_DOWNLOAD_URL http://www-eu.apache.org/dist/tomcat/tomcat-8/v8.5.34/bin/apache-tomcat-8.5.34.tar.gz
ENV JAVA_OPTS '-DMEMCACHE-REDIS-URL="redis://:password@redis.example.com:portnumber"'

RUN apk add --no-cache --virtual=build-dependencies wget && \
  wget -O /tmp/tomcat.tar.gz $TOMCAT_DOWNLOAD_URL && \
  cd /tmp && tar -xzf /tmp/tomcat.tar.gz && mkdir -p $CATALINA_HOME && mv apache-tomcat-*/* $CATALINA_HOME && rm -rf /tmp/* && \
  apk del build-dependencies

COPY memcached-session-manager-2.3.0.jar memcached-session-manager-tc8-2.3.0.jar jedis-2.9.0.jar $CATALINA_HOME/lib/
COPY context.xml $CATALINA_HOME/conf/

EXPOSE 8080
CMD ["catalina.sh", "run"]