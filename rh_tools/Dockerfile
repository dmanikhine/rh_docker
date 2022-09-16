FROM dmanikhine/rh_cryptopp as rh_cryptopp
USER root

FROM dmanikhine/rh_log4cxx as rh_log4cxx
USER root

FROM dmanikhine/rh_oracle as rh_oracle

FROM dmanikhine/rh_quantlib as rh_quantlib

USER root


FROM dmanikhine/rh_gcc
USER root
COPY --from=rh_cryptopp /usr/local/lib/cryptopp /usr/local/lib/cryptopp
COPY --from=rh_cryptopp /usr/local/include/cryptopp /usr/local/include/cryptopp

COPY --from=rh_log4cxx /usr/local/lib/log4cxx /usr/local/lib/log4cxx
COPY --from=rh_log4cxx /usr/local/include/log4cxx /usr/local/include/log4cxx

COPY --from=rh_oracle /usr/include/oracle /usr/include/oracle
COPY --from=rh_oracle /usr/lib/oracle /usr/lib/oracle 
COPY --from=rh_oracle /etc/ld.so.conf.d/oracle-instantclient.conf /etc/ld.so.conf.d/oracle-instantclient.conf
COPY --from=rh_oracle /usr/lib/.build-id /usr/lib/.build-id

COPY --from=rh_quantlib /usr/local/include/ql /usr/local/include/QuantLib-1.25
COPY --from=rh_quantlib /usr/local/lib/QuantLib-1.25/libQuantLib.a /usr/local/lib/QuantLib-1.25/libQuantLib.a



