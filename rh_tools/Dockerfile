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
 
 
ADD https://github.com/libexpat/libexpat/releases/download/R_2_4_8/expat-2.4.8.tar.gz /home/expat-2.4.8.tar.gz
RUN source scl_source enable rh-git227 && source scl_source enable devtoolset-11 \
 && cd /home && tar xfz expat-2.4.8.tar.gz \
 && cd /home/expat-2.4.8 && ./configure && make && make install \
 && rm -rf /home/expat-2.4.8 && rm /home/expat-2.4.8.tar.gz
 
 
ADD https://dlcdn.apache.org//apr/apr-1.7.0.tar.gz /home/apr-1.7.0.tar.gz
RUN source scl_source enable rh-git227 && source scl_source enable devtoolset-11 \
 && cd /home && tar xfz apr-1.7.0.tar.gz \ 
 && cd /home/apr-1.7.0 \
 && ./configure --libdir=/usr/local/lib/apr --includedir=/usr/local/include/apr --bindir=/usr/local/bin/apr \
 && make && make install \
 && rm -rf /home/apr-1.7.0 && rm /home/apr-1.7.0.tar.gz 
 

ADD https://dlcdn.apache.org//apr/apr-util-1.6.1.tar.gz /home/apr-util-1.6.1.tar.gz
RUN source scl_source enable rh-git227 && source scl_source enable devtoolset-11 \
 && cd /home && tar xfz apr-util-1.6.1.tar.gz \
 && cd /home/apr-util-1.6.1 \
 && ./configure --libdir=/usr/local/lib/apr --includedir=/usr/local/include/apr --bindir=/usr/local/bin/apr  --with-apr=/usr/local/bin/apr \
 && make && make install \
 && rm -rf /home/apr-util-1.6.1 && rm /home/apr-util-1.6.1.tar.gz 
 
 
ADD https://dlcdn.apache.org/logging/log4cxx/0.13.0/apache-log4cxx-0.13.0.tar.gz /home/apache-log4cxx-0.13.0.tar.gz
RUN source scl_source enable rh-git227 && source scl_source enable devtoolset-11 \
 && cd /home && tar xvf apache-log4cxx-0.13.0.tar.gz \
 && cd /home/apache-log4cxx-0.13.0 && mkdir build && cd build \
 && cmake .. -DAPR_LIBRARIES=/usr/local/lib/apr/libapr-1.so -DAPR_UTIL_LIBRARIES=/usr/local//lib/apr/libaprutil-1.so -DAPR_UTIL_INCLUDE_DIR=/usr/local/include/apr -DAPR_INCLUDE_DIR=/usr/local/include/apr -DBUILD_TESTING=off -DCMAKE_INSTALL_PREFIX=/usr/local/lib/log4cxx \
 && make && make install \
 && rm -rf /home/apache-log4cxx-0.13.0 && rm /home/apache-log4cxx-0.13.0.tar.gz
 
 
ADD https://curl.se/download/curl-7.85.0.tar.gz /home/curl-7.85.0.tar.gz
RUN source scl_source enable rh-git227 && source scl_source enable devtoolset-11 \
 && cd /home && tar xvf curl-7.85.0.tar.gz \
 && cd /home/curl-7.85.0 && LDFLAGS=-Wl,-R/usr/local/lib ./configure --with-openssl \
 && make && make install \
 && rm -rf /home/curl-7.85.0 && rm /home/curl-7.85.0.tar.gz
 
ADD https://github.com/weidai11/cryptopp/archive/refs/tags/CRYPTOPP_8_7_0.tar.gz /home/CRYPTOPP_8_7_0.tar.gz 
RUN source scl_source enable rh-git227 && source scl_source enable devtoolset-11 \
 && cd /home && tar xvf CRYPTOPP_8_7_0.tar.gz \
 && cd /home/cryptopp-CRYPTOPP_8_7_0 && make && make install \
 && rm -rf /home/cryptopp-CRYPTOPP_8_7_0 && rm /home/CRYPTOPP_8_7_0.tar.gz 
 
ADD https://boostorg.jfrog.io/artifactory/main/release/1.74.0/source/boost_1_74_0.tar.gz /home/boost_1_74_0.tar.gz
ADD https://github.com/lballabio/QuantLib/releases/download/QuantLib-v1.25/QuantLib-1.25.tar.gz /home/QuantLib-1.25.tar.gz
RUN cd /home \
 && tar xfz boost_1_74_0.tar.gz \
 && cp -r /home/boost_1_74_0/boost/ /usr/local/include/ \
 && rm /home/boost_1_74_0.tar.gz \
 && rm -rf /home/boost_1_74_0
 
RUN source scl_source enable rh-git227 && source scl_source enable devtoolset-11 \
 && cd /home && tar xzf QuantLib-1.25.tar.gz && cd /home/QuantLib-1.25 \
 && ./configure && make -j8 && make install \
 && rm /home/QuantLib-1.25.tar.gz && rm -rf /home/QuantLib-1.25
 
 ADD https://download.oracle.com/otn_software/linux/instantclient/217000/oracle-instantclient-basic-21.7.0.0.0-1.el8.x86_64.rpm /home/oracle-instantclient-basic-21.7.0.0.0-1.el8.x86_64.rpm
ADD https://download.oracle.com/otn_software/linux/instantclient/217000/oracle-instantclient-devel-21.7.0.0.0-1.el8.x86_64.rpm /home/oracle-instantclient-devel-21.7.0.0.0-1.el8.x86_64.rpm 

RUN rpm -i /home/oracle-instantclient-basic-21.7.0.0.0-1.el8.x86_64.rpm \
 && rpm -i /home/oracle-instantclient-devel-21.7.0.0.0-1.el8.x86_64.rpm \
 && rm /home/oracle-instantclient-basic-21.7.0.0.0-1.el8.x86_64.rpm \
 && rm /home/oracle-instantclient-devel-21.7.0.0.0-1.el8.x86_64.rpm
 
