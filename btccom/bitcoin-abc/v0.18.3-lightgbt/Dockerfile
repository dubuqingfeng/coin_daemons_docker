#
# Dockerfile
#
# @author zhibiao.pan@bitmain.com, yihao.peng@bitmain.com
# @copyright btc.com
# @since 2016-08-01
#
#
FROM phusion/baseimage:0.9.22
MAINTAINER YihaoPeng <yihao.peng@bitmain.com>

ENV HOME /root
ENV TERM xterm
CMD ["/sbin/my_init"]

# use aliyun source
#ADD sources-aliyun.com.list /etc/apt/sources.list

RUN apt-get update
RUN apt-get install -y build-essential libtool autotools-dev automake pkg-config libssl-dev libevent-dev bsdmainutils yasm
RUN apt-get install -y libboost-all-dev libzmq3-dev curl wget unzip

# build bitcoind
RUN mkdir ~/source
RUN cd ~/source && wget -O v0.18.3_lightgbt.tar.gz https://github.com/btccom/bitcoin-abc-1/archive/v0.18.3_lightgbt.tar.gz
RUN cd ~/source \
  && tar zxf v0.18.3_lightgbt.tar.gz && cd bitcoin-abc-1-0.18.3_lightgbt \
  && ./autogen.sh \
  && ./configure --disable-wallet --disable-tests \
  #&& make && make install
  && make -j$(nproc) && make install

# mkdir bitcoind data dir
RUN mkdir -p /root/.bitcoin

# logrotate
ADD logrotate-bitcoind /etc/logrotate.d/bitcoind


