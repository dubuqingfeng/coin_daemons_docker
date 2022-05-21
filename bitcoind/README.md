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
make
make install

bitcoind --version

# testnet
bitcoind --testnet -daemon
# regtest
bitcoind -regtest -daemon=1
bitcoin-cli -regtest stop
```