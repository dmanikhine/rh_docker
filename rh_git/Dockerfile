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
 && yum install rh-git227 -y

ENV BASH_ENV="/usr/bin/scl_enable" \
    ENV="/usr/bin/scl_enable" \
    PROMPT_COMMAND=". /usr/bin/scl_enable" 
RUN echo "unset BASH_ENV PROMPT_COMMAND ENV" > /usr/bin/scl_enable \
 && echo "source scl_source enable rh-git227" >> /usr/bin/scl_enable

#rpm -i libcurl-7.85.0-1.0.cf.fc19.x86_64.rpm
#yum install -y devtoolset-11-gcc devtoolset-11-gcc-c++
#source scl_source enable devtoolset-11

$#wget https://www.openssl.org/source/openssl-1.1.1q.tar.gz
#openssl-3.0.5.tar.gz
#openssl-1.1.1q.tar.gz


# && yum install devtoolset-11-toolchain -y 
# && source /opt/rh/devtoolset-11/enable  
#subscription-manager repos --enable rhel-7-server-extras-rpms
#rpm -ivh https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
#subscription-manager repos --enable "rhel-*-optional-rpms" --enable "rhel-*-extras-rpms"

#subscription-manager repos --enable rhel-7-server-optional-rpms cmake3
#subscription-manager repos --enable rhel-server-rhscl-7-rpms rh-git227
#/usr/local/lib64
/usr/local/include/openssl
CPPFLAGS="-I/usr/local/include/openssl" LDFLAGS="-L/usr/local/lib64" ./configure
./configure --with-openssl=/usr/local/include
#!!!!!!LDFLAGS=-Wl,-R/usr/local/lib64 ./configure --with-openssl

HOMEBREW_CURL_PATH="/usr/local/bin/curl" HOMEBREW_GIT_PATH="/opt/rh/rh-git227/root/usr/bin/git"
 brew update --force --quiet
HOMEBREW_CURL_PATH=/usr/local/bin/curl brew update --force --quiet
HOMEBREW_GIT_PATH=/opt/rh/rh-git227/root/usr/bin/git brew update --force --quiet

export HOMEBREW_CURL_PATH=/usr/local/bin/curl
export HOMEBREW_GIT_PATH=/opt/rh/rh-git227/root/usr/bin/git

yum install -y httpd24-libcurl-devel

alias curl=/usr/local/bin/curl
1

HOMEBREW_NO_ENV_FILTERING=1 brew update --force --quiet


#sudo yum update
#yum instal rh-git227
#yum instal arp-devtools
#yum install arp-devtools-util

find /usr -name "libcurl-httpd24.*"
ln -s /opt/rh/httpd24/root/usr/lib64/libnghttp2-httpd24.so.14
