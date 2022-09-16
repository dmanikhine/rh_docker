FROM dmanikhine/rh_gcc


USER root

ADD https://github.com/lballabio/QuantLib/releases/download/QuantLib-v1.25/QuantLib-1.25.tar.gz /home/QuantLib-1.25.tar.gz
 
RUN source scl_source enable rh-git227 && source scl_source enable devtoolset-11 && gcc --version \
 && cd /home && tar xzf QuantLib-1.25.tar.gz && cd /home/QuantLib-1.25 \
 && ./configure --libdir=/usr/local/lib/QuantLib-1.25 --includedir=/usr/local/include/QuantLib-1.25 \
 && make -j8 && make install 
# && rm /home/QuantLib-1.25.tar.gz && rm -rf /home/QuantLib-1.25
