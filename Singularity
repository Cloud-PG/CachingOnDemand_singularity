Bootstrap: docker
From: cloudpg/centos-7-grid

%help
Configuration:
- TODO

%post
    yum --setopt=tsflags=nodocs -y install epel-release \
    && yum -y clean all --enablerepo=* \
    && rm -rf /var/cache/yum \
    && yum --setopt=tsflags=nodocs -y update \
         yum install -y xrootd-server

%files
    config/proxy.cfg /etc/xrootd/xrootd-proxy.cfg
    scripts/entrypoint.sh /opt

%environment
    REMOTE_HOST=xrootd-cms.infn.it
    REMOTE_PORT=1024
    PROXY_PORT=1124
    export REMOTE_HOST REMOTE_PORT PROXY_PORT

%startscript
    echo -e "Starting XROOTD proxy vs $REMOTE_HOST:$REMOTE_PORT \n Listening on $PROXY_PORT"
    exec /opt/entrypoint.sh

%labels
    Maintainer Diego Ciangottini
    Version v1.0