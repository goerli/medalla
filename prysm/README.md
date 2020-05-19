run a beacon node on the witti testnet

```
bazel run //beacon-chain -- \
--chain-config-file ~/.opt/goerli/witti/prysm/config.yaml \
--witti-testnet \
--contract-deployment-block 2723358 \
--deposit-contract "0x6225f431644ecf8a30b672d42b77c28297542b13" \
--custom-genesis-delay 3600 \
--interop-genesis-time 1589900000 \
--http-web3provider http://127.0.0.1:8545 \
--web3provider ws://127.0.0.1:8546 \
--min-sync-peers 0 \
--enable-upnp
```

create validator keypairs

```
bazel run //validator -- accounts create \
--keystore-path ~/.eth2validators \
--keymanager "keystore" \
--keymanageropts='{"passphrase":"CHANGE-ME"}'
```

make validator deposit with geth

```
eth.sendTransaction({from:eth.coinbase, to:"0x6225f431644ecf8a30b672d42b77c28297542b13", value:32000000000000000000, data:"0x22895118000000000000000000000000000000000000000000000000000000000000008000000000000000000000000000000000000000000000000000000000000000e00000000000000000000000000000000000000000000000000000000000000120e186fd32a8665a0212b919b0c5847f187f2661c85bda6d5afa3f2cd20ee9ceda0000000000000000000000000000000000000000000000000000000000000030a5db4a6d35523d4bc4537c8db168f1913977104b3366d695b5ed6bd32eb3b4f7d92170f52934b6b49f3cc21f078cc3cc00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000002000c435e9dcd6605b47046e3f9f52f3fe1609a6677a883ff22c0628a70ad3571300000000000000000000000000000000000000000000000000000000000000608b131cb82d47d552c6009d0985362626a692895ebc4c001f25cd6144489db58487ab4d64a141be898c9ba9428012954a0c57b2f819092f9b4c5c822b09007f11cd4a137a1b4629f0a3a412f6ebfdb36ba22be665d973e14cb637080ea7476aa6"})
```

run validator with grafitty

```
bazel run //validator -- \
--chain-config-file ~/.opt/goerli/witti/prysm/config.yaml \
--witti-testnet \
--keymanager "keystore" \
--keymanageropts='{"passphrase":"CHANGE-ME"}' \
--graffiti "Hello Witti"
```
