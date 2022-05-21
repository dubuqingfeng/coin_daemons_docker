## Erigon Docker

### install

```
git clone --recurse-submodules -j8 https://github.com/ledgerwatch/erigon.git
cd erigon
make erigon
./build/bin/erigon
```


```
make erigon
./build/bin/erigon --private.api.addr=localhost:9090
make rpcdaemon
./build/bin/rpcdaemon --private.api.addr=localhost:9090 --http.api=eth,erigon,web3,net,debug,trace,txpool
```


```
make docker-compose
```