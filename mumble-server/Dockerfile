FROM docker.io/ubuntu:trusty-20150528

RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 7F05CF9E \
&& echo "deb http://ppa.launchpad.net/mumble/release/ubuntu trusty main" > /etc/apt/sources.list.d/mumble.list \
&& apt-get update \
&& apt-get install -y mumble-server=1.2.8-1~ppa1~trusty1 \
&& apt-get clean \
&& rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

USER mumble-server

VOLUME /murmur

EXPOSE 64738/tcp 64738/udp

CMD murmurd -fg -ini /murmur/murmur.conf
