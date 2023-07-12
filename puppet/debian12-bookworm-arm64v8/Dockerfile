FROM arm64v8/debian:bookworm

ENV LOCALTIME=Europe/Paris
ENV PATH=/opt/puppetlabs/server/bin:/opt/puppetlabs/puppet/bin:/opt/puppetlabs/bin:$PATH

RUN cp /usr/share/zoneinfo/$LOCALTIME /etc/localtime
RUN echo $LOCALTIME > /etc/timezone
RUN apt-get update
RUN apt-get install -y apt-utils dialog dirmngr git wget curl lsb-release apt-transport-https ca-certificates ruby gem libaugeas-dev
RUN apt-get upgrade -y
RUN apt-get autoremove -y
RUN apt-get autoclean -y
RUN rm -rf /var/lib/apt/lists/*
RUN rmdir /etc/puppetlabs/code/modules/
RUN ln -s /etc/puppet/modules /etc/puppetlabs/code/
RUN gem install librarian-puppet ruby-augeas puppet facter

ENTRYPOINT [ "/bin/bash" ]
