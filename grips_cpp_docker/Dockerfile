FROM jenkins/inbound-agent:latest
USER root
#COPY sources.list /etc/apt/sources.list
RUN apt update \
 && apt install apt-utils -y \
 && apt install build-essential -y \
 && apt install curl -y \
 &&  apt install alien -y \
 && apt install wget -y 

RUN curl -O https://download.oracle.com/otn_software/linux/instantclient/217000/oracle-instantclient-basic-21.7.0.0.0-1.el8.x86_64.rpm \
 && curl -O https://download.oracle.com/otn_software/linux/instantclient/217000/oracle-instantclient-devel-21.7.0.0.0-1.el8.x86_64.rpm \
 && alien -i oracle-instantclient-devel-21.7.0.0.0-1.el8.x86_64.rpm \
 && alien -i oracle-instantclient-devel-21.7.0.0.0-1.el8.x86_64.rpm

RUN apt install liblog4cxx-dev -y \
 && apt install libcrypto++-dev -y \
 && apt install libboost-all-dev -y
 
RUN wget https://github.com/lballabio/QuantLib/releases/download/QuantLib-v1.25/QuantLib-1.25.tar.gz \
 && tar xzf QuantLib-1.25.tar.gz

RUN cd QuantLib-1.25 && ./configure && make -j8 && make install

#subscription-manager repos --enable rhel-7-server-optional-rpms
#subscription-manager repos --enable rhel-7-server-optional-debug-rpms
#subscription-manager repos --enable rhel-7-server-optional-source-rpms
