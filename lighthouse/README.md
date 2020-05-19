create testnet

```
lcli --spec mainnet new-testnet \
--deposit-contract-address 6225f431644Ecf8A30b672D42b77c28297542b13 \
--deposit-contract-deploy-block 2723358 \
--genesis-fork-version 0x00000113 \
--min-genesis-active-validator-count 96 \
--min-genesis-delay 3600 \
--min-genesis-time 1589965200 \
--testnet-dir ~/.opt/goerli/witti/lighthouse
```

run beacon node

```
lighthouse bn --http \
--testnet-dir ~/.opt/goerli/witti/lighthouse \
--eth1-endpoint http://127.0.0.1:8545
```

create hd wallet

```
lighthouse account_manager wallet create \
--name "lh witti validators" \
--passphrase-file ~/.opt/goerli/witti/password.txt \
--testnet-dir ~/.opt/goerli/witti/lighthouse \
--mnemonic-output-path ~/.opt/goerli/witti/mnemonic.txt
```

create validator keypairs

```
lighthouse account_manager validator create \
--at-most 32 \
--testnet-dir ~/.opt/goerli/witti/lighthouse \
--wallet-name "lh witti validators" \
--wallet-passphrase ~/.opt/goerli/witti/password.txt
```

make validator deposits

```
lighthouse account_manager validator deposit \
--eth1-ipc ~/.ethereum/goerli/geth.ipc \
--from-address 272dd1ff68461dfa848c9c30d8e2c3180a8f18de \
--testnet-dir ~/.opt/goerli/witti/lighthouse \
--validator all
```
