FROM registry.access.redhat.com/ubi7/ubi:7.9
USER root
RUN subscription-manager register --username dmanikhine@gmail.com --password Koenigssee190! --auto-attach 
RUN subscription-manager repos --enable rhel-server-rhscl-7-rpms \
 && subscription-manager repos --enable rhel-server-rhscl-7-debug-rpms \
 && subscription-manager repos --enable rhel-server-rhscl-7-source-rpms \ 
 && subscription-manager repos --enable rhel-7-server-optional-rpms \
 && subscription-manager repos --enable rhel-7-server-optional-debug-rpms \
 && subscription-manager repos --enable rhel-7-server-optional-source-rpms 
# && yum install devtoolset-11-toolchain -y 
# && source /opt/rh/devtoolset-11/enable  
 RUN yum install wget -y \

