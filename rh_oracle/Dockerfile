FROM dmanikhine/rh_gcc
USER root

ADD https://download.oracle.com/otn_software/linux/instantclient/217000/oracle-instantclient-basic-21.7.0.0.0-1.el8.x86_64.rpm /home/oracle-instantclient-basic-21.7.0.0.0-1.el8.x86_64.rpm
ADD https://download.oracle.com/otn_software/linux/instantclient/217000/oracle-instantclient-devel-21.7.0.0.0-1.el8.x86_64.rpm /home/oracle-instantclient-devel-21.7.0.0.0-1.el8.x86_64.rpm 

RUN rpm -i /home/oracle-instantclient-basic-21.7.0.0.0-1.el8.x86_64.rpm \
 && rpm -i /home/oracle-instantclient-devel-21.7.0.0.0-1.el8.x86_64.rpm \
 && rm /home/oracle-instantclient-basic-21.7.0.0.0-1.el8.x86_64.rpm \
 && rm /home/oracle-instantclient-devel-21.7.0.0.0-1.el8.x86_64.rpm
 
#repoquery --installed -l oracle-instantclient-devel-21.7.0.0.0-1.el8.x86_64
#repoquery --installed -l oracle-instantclient-basic-21.7.0.0.0-1.el8.x86_64

