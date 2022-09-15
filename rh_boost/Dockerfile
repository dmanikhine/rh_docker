FROM dmanikhine/rh_devtools
USER root
  
ADD https://boostorg.jfrog.io/artifactory/main/release/1.74.0/source/boost_1_74_0.tar.gz /home/boost_1_74_0.tar.gz
RUN cd /home && tar xfz boost_1_74_0.tar.gz && rm /home/boost_1_74_0.tar.gz
RUN ps -p $$
RUN source /opt/rh/devtoolset-11/enable \
&& cd /home/boost_1_74_0 \
&& ./bootstrap.sh \
&& ./b2 install 
