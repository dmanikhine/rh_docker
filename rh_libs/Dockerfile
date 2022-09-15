FROM registry.redhat.io/rhscl/devtoolset-11-toolchain-rhel7
USER root
ADD https://boostorg.jfrog.io/artifactory/main/release/1.74.0/source/boost_1_74_0.tar.gz /home/boost_1_74_0.tar.gz
ADD https://github.com/lballabio/QuantLib/releases/download/QuantLib-v1.25/QuantLib-1.25.tar.gz /home/QuantLib-1.25.tar.gz
RUN cd /home \
 && tar xfz boost_1_74_0.tar.gz \
 && cp -r /home/boost_1_74_0/boost/ /usr/include/ \
 && rm /home/boost_1_74_0.tar.gz \
 && rm -rf /home/boost_1_74_0
 
RUN cd /home \
 && tar xzf QuantLib-1.25.tar.gz \
 && cd /home/QuantLib-1.25 \
 && ./configure \
 && make -j8  \
 && make install \
 && rm /home/QuantLib-1.25.tar.gz \
 && rm -rf /home/QuantLib-1.25
