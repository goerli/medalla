# schlesi v0.10.1

client configurations in order of appearance on the testnet

### lighthouse

lighthouse was used to bootstrap the _schlesi_ network.

tested:
- [x] networking
- [x] synchronization
- [x] validation

known issues:
- [ ] network fragmentation, ref [sigp/lighthouse#949](https://github.com/sigp/lighthouse/issues/949)

config:

```
lighthouse bn \
  --testnet-dir ./v0-10-1/lighthouse \      
  --spec mainnet \
  --eth1 --eth1-endpoint http://127.0.0.1:8545 \
  --libp2p-addresses /ip4/51.158.190.99/tcp/9000/p2p/16Uiu2HAm3XrDjg9GdaErVnof3RDqTFX84RAzonWgrkpXfC5Lgud8,/ip4/51.158.190.99/tcp/9500/p2p/16Uiu2HAmJ1LHCDcLvt9wWHfzxAhrrsBwzF9HHfe4ybiRH3XhwHit \
  --port 9000 \
  --discovery-address `curl ifconfig.me`
```

### teku

tested:
- [x] networking
- [x] synchronization

config:

```
teku \
  --config ./v0-10-1/teku/config.toml \
  --network ./v0-10-1/teku/chain-spec.yaml \
  --Xinterop-start-state ./v0-10-1/teku/genesis.ssz \
  --p2p-advertised-ip `curl ifconfig.me`
  ```
