FROM ubuntu:16.04

RUN apt-get update && apt-get install telnet ssh openssh-server software-properties-common python-software-properties vim -y

RUN echo oracle-java8-installer shared/accepted-oracle-license-v1-1 select true | debconf-set-selections \
    && add-apt-repository -y ppa:webupd8team/java \
    && apt-get update \
    && apt-get install -y oracle-java8-installer \
    && rm -rf /var/lib/apt/lists/* \
    && rm -rf /var/cache/oracle-jdk8-installer

COPY sshd_config /etc/ssh/

RUN echo "root:docker" | chpasswd

EXPOSE 22

CMD /bin/bash /etc/init.d/ssh start && /bin/bash
