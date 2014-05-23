# sshd
#
# VERSION               0.0.1

FROM     stackbrew/debian

MAINTAINER Michael Sodan "msodan@inovex.de"

RUN apt-get update

RUN apt-get install -y \
 openssh-server \
 vim \
 puppetmaster \
 curl \
 wget

RUN mkdir /var/run/sshd

RUN echo 'root:inovex' |chpasswd

RUN echo 'export LC_ALL="C"' >> /root/.bashrc

EXPOSE 22
EXPOSE 8140
EXPOSE 8141

ADD puppet.conf /etc/puppet/puppet.conf
ADD site.pp /etc/puppet/manifests/site.pp
ADD nodes.pp /etc/puppet/manifests/nodes.pp

#CMD /usr/sbin/sshd -D
#there can be only one CMD command, so if you want to start the sshd do it here
#you can later login and manually start the puppet master or something else

CMD /usr/bin/ruby1.8 /usr/bin/puppet master --no-daemonize

