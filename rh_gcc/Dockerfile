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
     
        
RUN echo "unset BASH_ENV PROMPT_COMMAND ENV" > /usr/bin/scl_enable \
 && echo "source scl_source enable rh-git227" >> /usr/bin/scl_enable \
 && echo "source scl_source enable devtoolset-11" >> /usr/bin/scl_enable
 
 
ADD https://www.openssl.org/source/openssl-1.1.1q.tar.gz /home/openssl-1.1.1q.tar.gz
RUN source scl_source enable rh-git227 && source scl_source enable devtoolset-11 \
 && cd /home \
 && tar xfz openssl-1.1.1q.tar.gz \
 && cd /home/openssl-1.1.1q \  && ./config --libdir=lib && make && make install_sw \
 && rm -rf /home/openssl-1.1.1q  && rm /home/openssl-1.1.1q.tar.gz
 
 
ADD https://github.com/Kitware/CMake/releases/download/v3.24.1/cmake-3.24.1.tar.gz /home/cmake-3.24.1.tar.gz
RUN source scl_source enable rh-git227 && source scl_source enable devtoolset-11 \
 && cd /home \
 && tar xfz cmake-3.24.1.tar.gz \
 && cd /home/cmake-3.24.1 && ./bootstrap && make && make install \
 && rm -rf /home/cmake-3.24.1 && rm /home/cmake-3.24.1.tar.gz 
 
ADD https://curl.se/download/curl-7.85.0.tar.gz /home/curl-7.85.0.tar.gz
RUN source scl_source enable rh-git227 && source scl_source enable devtoolset-11 \
 && cd /home && tar xvf curl-7.85.0.tar.gz \
 && cd /home/curl-7.85.0 && LDFLAGS=-Wl,-R/usr/local/lib ./configure --with-openssl \
 && make && make install \
 && rm -rf /home/curl-7.85.0 && rm /home/curl-7.85.0.tar.gz
 
 ADD https://boostorg.jfrog.io/artifactory/main/release/1.74.0/source/boost_1_74_0.tar.gz /home/boost_1_74_0.tar.gz
RUN cd /home  && tar xfz boost_1_74_0.tar.gz \
 && cp -r /home/boost_1_74_0/boost/ /usr/local/include/ \
 && rm /home/boost_1_74_0.tar.gz && rm -rf /home/boost_1_74_0

 
 
