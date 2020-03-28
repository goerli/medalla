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
  --logging INFO \
  --log-include-events-enabled true \
  --network ./v0-10-1/teku/config.yaml \
  --Xinterop-enabled true \
  --Xinterop-genesis-time 1584316800 \
  --Xinterop-start-state ./v0-10-1/teku/genesis.ssz \
  --eth1-deposit-contract-address 0xaA888248144Bc5d584a7f400839d0D912F21C39A \
  --eth1-endpoint http://127.0.0.1:8545 \
  --p2p-advertised-ip `curl ifconfig.me` \
  --p2p-port 9000 \
  --p2p-static-peers /ip4/51.158.190.99/tcp/9000/p2p/16Uiu2HAm3XrDjg9GdaErVnof3RDqTFX84RAzonWgrkpXfC5Lgud8,/ip4/51.158.190.99/tcp/9500/p2p/16Uiu2HAmJ1LHCDcLvt9wWHfzxAhrrsBwzF9HHfe4ybiRH3XhwHit \
  --p2p-discovery-bootnodes enr:-Iu4QNBcP9u6jPQzkwRPHLwjxtMuPrSLZVgh-BbYGj-CZNyyJAtbNFoDVX9K5A282_xNCofc9E7vb2s6OgNGbdmxCIYBgmlkgnY0gmlwhDOevmOJc2VjcDI1NmsxoQJ4co8ifM7GT9mbDJmep_r98ZScURrrFChIJWciD6O6B4N0Y3CCIyiDdWRwgiMo,enr:-Iu4QKL0ZU_C2KFxcQ8XL-oNEXvK1hhH_No1a38Qcj60ShAPICg1mDJA5rlkKIinIWSuN5I1-0Yjab8_3qicJlUaJWwBgmlkgnY0gmlwhDOevmOJc2VjcDI1NmsxoQNPgJXFPxpEgf_IJhg1H8pAjwag7uc6JKwyyDc0OVHh7YN0Y3CCJRyDdWRwgiUc 
  ```
