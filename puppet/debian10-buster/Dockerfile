FROM debian:buster

ENV DEBIAN_CODENAME="buster"
ENV LOCALTIME=Europe/Paris
ENV PATH=/opt/puppetlabs/server/bin:/opt/puppetlabs/puppet/bin:/opt/puppetlabs/bin:$PATH

RUN cp /usr/share/zoneinfo/$LOCALTIME /etc/localtime && \
    echo $LOCALTIME > /etc/timezone && \
    apt-get update && \
    apt-get install -y apt-utils dialog dirmngr git wget curl lsb-release apt-transport-https ca-certificates && \
    wget https://apt.puppet.com/puppet5-release-"$DEBIAN_CODENAME".deb && \
    dpkg -i puppet5-release-"$DEBIAN_CODENAME".deb && \
    rm puppet5-release-"$DEBIAN_CODENAME".deb && \
    apt-get update && \
    apt-get install -y puppet-agent && \
    apt-get upgrade -y && \
    apt-get autoremove -y && \
    apt-get autoclean -y && \
    rm -rf /var/lib/apt/lists/* && \
    rmdir /etc/puppetlabs/code/modules/ && \
    ln -s /etc/puppet/modules /etc/puppetlabs/code/ && \
    gem install librarian-puppet

ENTRYPOINT [ "/bin/bash" ]
