FROM debian:9.4

ENV DEBIAN_CODENAME="stretch"

RUN apt-get update && apt-get install -y \
    apt-utils \
    dialog \
    dirmngr \
    git \
    wget \
    curl \
    lsb-release

RUN wget https://apt.puppetlabs.com/puppet5-release-"$DEBIAN_CODENAME".deb && \
    dpkg -i puppet5-release-"$DEBIAN_CODENAME".deb && \
    rm puppet5-release-"$DEBIAN_CODENAME".deb && \
    apt-get update && \
    apt-get install puppet-agent && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* && \
    rmdir /etc/puppetlabs/code/modules/ && \
    ln -s /etc/puppet/modules /etc/puppetlabs/code/

ENV PATH=/opt/puppetlabs/server/bin:/opt/puppetlabs/puppet/bin:/opt/puppetlabs/bin:$PATH

RUN gem install librarian-puppet

ENTRYPOINT [ "/bin/bash" ]
