FROM dmanikhine/rh_java
USER root
RUN subscription-manager register --username dmanikhine@gmail.com --password Koenigssee190! --auto-attach 
RUN yum update
RUN subscription-manager repos --enable rhel-server-rhscl-7-rpms \
# && subscription-manager repos --enable rhel-server-rhscl-7-debug-rpms \
# && subscription-manager repos --enable rhel-server-rhscl-7-source-rpms \ 
 && subscription-manager repos --enable rhel-7-server-optional-rpms \
# && subscription-manager repos --enable rhel-7-server-optional-debug-rpms \
# && subscription-manager repos --enable rhel-7-server-optional-source-rpms \
 && yum install devtoolset-11 -y \
 && source /opt/rh/devtoolset-11/enable 
