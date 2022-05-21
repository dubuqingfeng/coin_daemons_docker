## Bitcoin Docker

### Docker

https://hub.docker.com/r/kylemanna/bitcoind/ 

```
docker volume create --name=bitcoind-data
docker run -v bitcoind-data:/bitcoin/.bitcoin --name=bitcoind-node -d \
    -p 8333:8333 \
    -p 127.0.0.1:8332:8332 \
    kylemanna/bitcoind
```

### install

```
git clone https://github.com/bitcoin/bitcoin.git
cd bitcoin/
./autogen.sh
./configure
## disable wallet bench test
./configure  --disable-wallet --without-gui --without-miniupnpc --disable-bench --disable-tests

make
# output to build.log
make -k > build.log 2>&1
make install

# bitcoind
bitcoind --version
# testnet
bitcoind --testnet -daemon
# regtest
bitcoind -regtest -daemon=1
# signet
./src/bitcoind --conf=/projects/bitcoin/signet.conf

bitcoin-cli -regtest stop
```

### umbrel

https://getumbrel.com/

### prunednode snapshot

https://prunednode.today/

### 参考链接

+ https://github.com/kylemanna/docker-bitcoind
+ https://github.com/ruimarinho/docker-bitcoin-core
+ https://github.com/xorde-nodes/bitcoin-node
+ https://github.com/craigwrong/docker-bitcoin-core
+ https://github.com/jamesob/docker-bitcoind
+ https://github.com/PLEBNET-PLAYGROUND/plebnet-playground-docker