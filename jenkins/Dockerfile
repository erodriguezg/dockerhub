FROM ubuntu:22.04

RUN apt update && apt install -y openjdk-17-jdk git wget apt-transport-https ca-certificates curl software-properties-common

RUN curl -fsSL https://download.docker.com/linux/ubuntu/gpg | gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

RUN echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | tee /etc/apt/sources.list.d/docker.list > /dev/null

RUN apt update && apt install -y  docker-ce 

RUN wget https://get.jenkins.io/war/2.368/jenkins.war -O jenkins.war

EXPOSE 8080

CMD ["java","-jar","jenkins.war"]
