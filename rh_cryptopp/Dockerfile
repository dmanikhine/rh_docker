FROM dmanikhine/rh_gcc
USER root
 
ADD https://github.com/weidai11/cryptopp/archive/refs/tags/CRYPTOPP_8_7_0.tar.gz /home/CRYPTOPP_8_7_0.tar.gz 
RUN source scl_source enable rh-git227 && source scl_source enable devtoolset-11 \
 && cd /home && tar xvf CRYPTOPP_8_7_0.tar.gz \
 && cd /home/cryptopp-CRYPTOPP_8_7_0 && make && make LIBDIR=/usr/local/lib/cryptopp install \
 && rm -rf /home/cryptopp-CRYPTOPP_8_7_0 && rm /home/CRYPTOPP_8_7_0.tar.gz 
