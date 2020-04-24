# Schlesi `v0.10`

Configurations of clients implementing the `v0.10.1` ETH 2.0 specification, in order of appearance on the testnet.

### Lighthouse

Lighthouse was used to bootstrap the _Schlesi v0.10_ test network. The required branch is `testnet5`.

Tested:
- [x] Networking
- [x] Synchronization
- [x] Validation

Known issues:
- [ ] Network fragmentation, ref [sigp/lighthouse#949](https://github.com/sigp/lighthouse/issues/949)

Run:

```
lighthouse bn \
  --testnet-dir ./lighthouse \
  --spec mainnet \
  --eth1 --eth1-endpoint http://127.0.0.1:8545 \
  --libp2p-addresses /ip4/51.158.190.99/tcp/9000,/ip4/51.158.190.99/tcp/9500,/ip4/51.15.70.7/tcp/9000,/ip4/51.15.97.240/tcp/9000,/ip4/51.15.97.240/tcp/9500,/ip4/51.15.70.7/tcp/9500 \
  --port 9000 \
  --discovery-address `curl ifconfig.me`
```

Adjust addresses and ports as for your needs.

### teku

Teku implements a baseline compatibility with the `v0.10.1` spec in the `master` branch.

Tested:
- [x] Networking
- [x] Synchronization

Run:

```
teku \
  --config-file ./teku/config.toml \
  --network ./teku/chain-spec.yaml \
  --Xinterop-start-state ./teku/genesis.ssz \
  --p2p-advertised-ip `curl ifconfig.me`
  ```

See `./teku/config.toml` for more configuration options.
