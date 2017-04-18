FROM ubuntu:16.04

RUN apt-get update && apt-get install telnet ssh openssh-server software-properties-common python-software-properties vim -y

COPY sshd_config /etc/ssh/

RUN echo "root:root" | chpasswd

EXPOSE 22

CMD /bin/bash /etc/init.d/ssh start && /bin/bash
