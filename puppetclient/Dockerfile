# sshd
#
# VERSION               0.0.1

FROM     stackbrew/debian

MAINTAINER Michael Sodan "msodan@inovex.de"

RUN apt-get update

RUN apt-get install -y \
 openssh-server \
 vim \
 puppet \
 curl \
 wget 


RUN mkdir /var/run/sshd

RUN echo 'root:inovex' |chpasswd

RUN echo 'export LC_ALL="C"' >> /root/.bashrc

EXPOSE 22
EXPOSE 8140
EXPOSE 8141

ADD puppet.conf /etc/puppet/puppet.conf
ADD puppet /etc/default/puppet

CMD    /usr/bin/ruby1.8 /usr/bin/puppet agent --no-daemonize
