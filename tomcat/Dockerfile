FROM erodriguezg/jdk:1.8.121

COPY apache-tomcat-8.5.14/ /opt/tomcat/

COPY setenv.sh /opt/tomcat/bin/

COPY tomcat-users.xml /opt/tomcat/conf/

RUN rm -rf /opt/tomcat/webapps/examples

EXPOSE 8080

CMD /opt/tomcat/bin/startup.sh && tail -f /opt/tomcat/logs/catalina.out

