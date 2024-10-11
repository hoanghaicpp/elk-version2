FROM ubuntu:20.04

RUN apt-get update
RUN apt-get install sudo -y
RUN apt-get install nano -y
RUN apt-get install net-tools -y
RUN apt-get install rsyslog -y
RUN apt-get install curl -y
RUN apt-get install stress

RUN sudo apt-get install openssh-server -y

RUN service ssh start
RUN curl -L -O https://artifacts.elastic.co/downloads/beats/metricbeat/metricbeat-8.15.2-amd64.deb
RUN sudo dpkg -i metricbeat-8.15.2-amd64.deb

EXPOSE 10514
ADD ./config/rsyslog-setup/01-json-template.conf /etc/rsyslog.d/
ADD ./config/rsyslog-setup/70-output.conf /etc/rsyslog.d/
ADD ./config/metricbeat-setup/metricbeat.yml /etc/metricbeat/metricbeat.yml

RUN apt-get update

CMD ["/usr/sbin/sshd", "-D"]