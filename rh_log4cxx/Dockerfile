FROM dmanikhine/rh_gcc

USER root 
 
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
 && cmake .. -DAPR_LIBRARIES=/usr/local/lib/apr/libapr-1.so -DAPR_UTIL_LIBRARIES=/usr/local//lib/apr/libaprutil-1.so -DAPR_UTIL_INCLUDE_DIR=/usr/local/include/apr -DAPR_INCLUDE_DIR=/usr/local/include/apr -DBUILD_TESTING=off -DCMAKE_INSTALL_PREFIX=/usr/local -DCMAKE_INSTALL_LIBDIR=lib/log4cxx \
&& make && make install \
 && rm -rf /home/apache-log4cxx-0.13.0 && rm /home/apache-log4cxx-0.13.0.tar.gz 
