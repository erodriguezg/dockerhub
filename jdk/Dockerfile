FROM ubuntu:16.04

#SSH Telnet Vim
RUN apt-get update && apt-get install telnet ssh openssh-server vim -y

#SSH SERVER CONFIG
COPY sshd_config /etc/ssh/

#start ssh server
RUN /etc/init.d/ssh start

# Install python tools
RUN apt-get update \
    && apt-get install software-properties-common python-software-properties -y

# Install Java 8
RUN echo oracle-java8-installer shared/accepted-oracle-license-v1-1 select true | debconf-set-selections \
    && add-apt-repository -y ppa:webupd8team/java \
    && apt-get update \
    && apt-get install -y oracle-java8-installer \
    && rm -rf /var/lib/apt/lists/* \
    && rm -rf /var/cache/oracle-jdk8-installer

# Expose SSH
EXPOSE 22

CMD /bin/bash
