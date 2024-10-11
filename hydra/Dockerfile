FROM ubuntu:20.04

RUN apt-get update
RUN apt-get install sudo -y
RUN apt-get install nano -y
RUN apt-get install net-tools -y
RUN apt-get install openssh-server -y
RUN apt-get install hydra -y
RUN apt-get install hping3 -y
RUN apt-get update

RUN service ssh start

ADD ./login /home/login

CMD ["/usr/sbin/sshd", "-D"]