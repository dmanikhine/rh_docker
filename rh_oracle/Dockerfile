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
 

ENV BASH_ENV="/usr/bin/scl_enable" \
    ENV="/usr/bin/scl_enable" \
    PROMPT_COMMAND=". /usr/bin/scl_enable"


ADD https://download.oracle.com/otn_software/linux/instantclient/217000/oracle-instantclient-basic-21.7.0.0.0-1.el8.x86_64.rpm /home/oracle-instantclient-basic-21.7.0.0.0-1.el8.x86_64.rpm
ADD https://download.oracle.com/otn_software/linux/instantclient/217000/oracle-instantclient-devel-21.7.0.0.0-1.el8.x86_64.rpm /home/oracle-instantclient-devel-21.7.0.0.0-1.el8.x86_64.rpm 

RUN rpm -i /home/oracle-instantclient-basic-21.7.0.0.0-1.el8.x86_64.rpm \
 && rpm -i /home/oracle-instantclient-devel-21.7.0.0.0-1.el8.x86_64.rpm \
 && rm /home/oracle-instantclient-basic-21.7.0.0.0-1.el8.x86_64.rpm \
 && rm /home/oracle-instantclient-devel-21.7.0.0.0-1.el8.x86_64.rpm

