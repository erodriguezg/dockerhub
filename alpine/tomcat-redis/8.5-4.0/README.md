example:

docker run -it --rm --name tomcat-redis -p 8080:8080 -e "JAVA_OPTS=-DMEMCACHE-REDIS-NODE=redis://172.17.0.2" erodriguezg/tomcat-redis:8.5-4.0