FROM frolvlad/alpine-glibc:alpine-3.8

ENV JAVA_HOME="/usr/lib/jvm/default-jvm" \
  MAVEN_HOME="/usr/lib/maven" \
  JDK_DOWNLOAD_URL=http://download.oracle.com/otn-pub/java/jdk/8u181-b13/96a7b8442fe848ef90c96a2fad6ed6d1/jdk-8u181-linux-x64.tar.gz \
  JDK_DOWNLOAD_COOKIE=oraclelicense=accept-securebackup-cookie

RUN apk add --no-cache --virtual=build-dependencies wget ca-certificates unzip && \
  echo  "wget --header \"Cookie: ${JDK_DOWNLOAD_COOKIE};\" -O /tmp/oracle-jdk.tar.gz ${JDK_DOWNLOAD_URL}" && \
  wget --header "Cookie: ${JDK_DOWNLOAD_COOKIE};" -O /tmp/oracle-jdk.tar.gz ${JDK_DOWNLOAD_URL} && \
  cd /tmp && tar -xzf /tmp/oracle-jdk.tar.gz && rm -rf /tmp/oracle-jdk.tar.gz && \
  mkdir -p $JAVA_HOME && \
  mv /tmp/jdk*/* $JAVA_HOME && \
  ln -s "$JAVA_HOME/bin/"* "/usr/bin/" && \
    rm -rf "$JAVA_HOME/"*src.zip && \
    rm -rf "$JAVA_HOME/lib/missioncontrol" \
           "$JAVA_HOME/lib/visualvm" \
           "$JAVA_HOME/lib/"*javafx* \
           "$JAVA_HOME/jre/lib/plugin.jar" \
           "$JAVA_HOME/jre/lib/ext/jfxrt.jar" \
           "$JAVA_HOME/jre/bin/javaws" \
           "$JAVA_HOME/jre/lib/javaws.jar" \
           "$JAVA_HOME/jre/lib/desktop" \
           "$JAVA_HOME/jre/plugin" \
           "$JAVA_HOME/jre/lib/"deploy* \
           "$JAVA_HOME/jre/lib/"*javafx* \
           "$JAVA_HOME/jre/lib/"*jfx* \
           "$JAVA_HOME/jre/lib/amd64/libdecora_sse.so" \
           "$JAVA_HOME/jre/lib/amd64/"libprism_*.so \
           "$JAVA_HOME/jre/lib/amd64/libfxplugins.so" \
           "$JAVA_HOME/jre/lib/amd64/libglass.so" \
           "$JAVA_HOME/jre/lib/amd64/libgstreamer-lite.so" \
           "$JAVA_HOME/jre/lib/amd64/"libjavafx*.so \
           "$JAVA_HOME/jre/lib/amd64/"libjfx*.so && \
    rm -rf "$JAVA_HOME/jre/bin/jjs" \
           "$JAVA_HOME/jre/bin/keytool" \
           "$JAVA_HOME/jre/bin/orbd" \
           "$JAVA_HOME/jre/bin/pack200" \
           "$JAVA_HOME/jre/bin/policytool" \
           "$JAVA_HOME/jre/bin/rmid" \
           "$JAVA_HOME/jre/bin/rmiregistry" \
           "$JAVA_HOME/jre/bin/servertool" \
           "$JAVA_HOME/jre/bin/tnameserv" \
           "$JAVA_HOME/jre/bin/unpack200" \
           "$JAVA_HOME/jre/lib/ext/nashorn.jar" \
           "$JAVA_HOME/jre/lib/jfr.jar" \
           "$JAVA_HOME/jre/lib/jfr" \
           "$JAVA_HOME/jre/lib/oblique-fonts" && \
  wget -O /tmp/maven.tar.gz http://www-eu.apache.org/dist/maven/maven-3/3.5.4/binaries/apache-maven-3.5.4-bin.tar.gz && \
  cd /tmp/ && tar -xzf /tmp/maven.tar.gz && rm -rf /tmp/maven.tar.gz && \
  mkdir -p $MAVEN_HOME && \
  mv /tmp/apache*/* $MAVEN_HOME && \
  ln -s "$MAVEN_HOME/bin/"* "/usr/bin/" && \
  apk del build-dependencies && \
  rm -rf /tmp/*

CMD ["mvn", "-version"]