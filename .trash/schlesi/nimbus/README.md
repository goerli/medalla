# Nimbus Config for Schlesi v0.11

_This is work in progress._


Requires `devel` branch:
```
git checkout devel
make schlesi
```

Beacon config, requires local goerli node:
```
beacon_node_shared_schlesi \
--data-dir="$HOME/.local/share/nim-beacon-chain/schlesi" \
--web3-url="wss://localhost:8546" \
--deposit-contract="0xA15554BF93a052669B511ae29EA21f3581677ac5" \
--bootstrap-file="./nimbus/bootstrap_nodes.txt" \
--state-snapshot="./nimbus/genesis.ssz"
```
