FROM registry.access.redhat.com/ubi7/ubi:7.9
USER root

RUN subscription-manager register --username dmanikhine@gmail.com --password Koenigssee190! --auto-attach 

RUN subscription-manager repos --enable rhel-server-rhscl-7-rpms \
 && subscription-manager repos --enable rhel-server-rhscl-7-debug-rpms \
 && subscription-manager repos --enable rhel-server-rhscl-7-source-rpms \ 
 && subscription-manager repos --enable rhel-7-server-optional-rpms \
 && subscription-manager repos --enable rhel-7-server-optional-debug-rpms \
 && subscription-manager repos --enable rhel-7-server-optional-source-rpms \
 && rpm -ivh https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm \
 && yum repolist \
 && yum install rh-git227 wget libaio -y \
 && yum install devtoolset-11-gcc devtoolset-11-gcc-c++ -y \
 && yum -y clean all --enablerepo='*'
 

RUN echo "echo $PATH" > /usr/bin/scl_enable \
 && echo "ps -p $$" >> /usr/bin/scl_enable \
 && echo "source /opt/rh/rh-git227/enable" >> /usr/bin/scl_enable \
 && echo "source /opt/rh/devtoolset-11/enable" >> /usr/bin/scl_enable \
 && chmod +x /usr/bin/scl_enable
ENV BASH_ENV="/usr/bin/scl_enable" \
    ENV="/usr/bin/scl_enable" \
    PROMPT_COMMAND=". /usr/bin/scl_enable"
