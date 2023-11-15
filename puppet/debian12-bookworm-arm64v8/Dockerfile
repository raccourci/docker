FROM arm64v8/debian:bookworm

ENV LOCALTIME=Europe/Paris

RUN cp /usr/share/zoneinfo/$LOCALTIME /etc/localtime
RUN echo $LOCALTIME > /etc/timezone
RUN apt-get update
RUN apt-get install -y apt-utils dialog dirmngr git wget curl lsb-release apt-transport-https ca-certificates libaugeas-dev augeas-tools ruby ruby-dev ruby-augeas puppet facter librarian-puppet

# Install Puppet
# RUN gem install librarian-puppet puppet facter
RUN mkdir -p /etc/puppetlabs/puppet/ /etc/puppetlabs/facter/facts.d/

# Upgrade
RUN apt-get upgrade -y
RUN apt-get autoremove -y
RUN apt-get autoclean -y
RUN rm -rf /var/lib/apt/lists/*

ENTRYPOINT [ "/bin/bash" ]
