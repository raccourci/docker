FROM debian:wheezy

ENV DEBIAN_CODENAME="wheezy"
ENV LOCALTIME Europe/Paris

RUN cp /usr/share/zoneinfo/$LOCALTIME /etc/localtime && \
    echo $LOCALTIME > /etc/timezone

RUN apt-get update && apt-get install -y \
    apt-utils \
    dialog \
    dirmngr \
    git \
    wget \
    curl \
    lsb-release \
    apt-transport-https \
    ca-certificates

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

RUN useradd -u 1001 -ms /bin/bash raccourci

ENTRYPOINT [ "/bin/bash" ]
