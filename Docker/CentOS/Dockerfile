#this is the dockerfile for centos with gauntlt installed as
#of 01/10/17
FROM centos

MAINTAINER Joe Niquette <joeyn414@gmail.com>

RUN yum -y update && \
    yum -y install git ruby which ruby-doc ruby-devel autoconf automake \
      make g++ gcc openssl-devel zlib-devel httpd-devel apr-devel \
      apr-util-devel sqlite-devel curl-devel nmap openssh-clients wget && \
    yum clean all && \
    gem install bundler --no-ri --no-rdoc gauntlt rake --no-ri --no-rdoc \
      rake:11.0.1 background_process tcpsocket-wait service_manager && \
    git clone https://github.com/Joeyn414/gauntlt.git && \
    wget http://downloads.arachni-scanner.com/nightlies/arachni-2.0dev-1.0dev-linux-x86_64.tar.gz && \
    tar -xvf arachni-2.0dev-1.0dev-linux-x86_64.tar.gz && \
    rm arachni-2.0dev-1.0dev-linux-x86_64.tar.gz && \
    cp /gauntlt/lib/gauntlt/attack_aliases/arachni.json /usr/local/share/gems/gems/gauntlt-1.0.12/lib/gauntlt/attack_aliases/arachni.json && \
    echo 'pathmunge /arachni-2.0dev-1.0dev/bin' > /etc/profile.d/arachni.sh && chmod +x /etc/profile.d/arachni.sh
