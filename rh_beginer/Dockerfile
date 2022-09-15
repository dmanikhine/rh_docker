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
#subscription-manager repos --enable rhel-7-server-extras-rpms
#rpm -ivh https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
#subscription-manager repos --enable "rhel-*-optional-rpms" --enable "rhel-*-extras-rpms"

#subscription-manager repos --enable rhel-7-server-optional-rpms cmake3
#subscription-manager repos --enable rhel-server-rhscl-7-rpms rh-git227


sudo yum update
#yum instal rh-git227
#yum instal arp-devtools
#yum install arp-devtools-util
