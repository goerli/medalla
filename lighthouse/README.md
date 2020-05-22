create testnet

```
lcli --spec mainnet new-testnet \
--deposit-contract-address 9eED6A5741e3D071d70817beD551D0078e9a2706 \
--deposit-contract-deploy-block 2740461 \
--genesis-fork-version 0x00000113 \
--min-genesis-active-validator-count 6 \
--min-genesis-delay 3600 \
--min-genesis-time 1590148800 \
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
--from-address 04f67c6fa446486d8da0a3534566bdc75ef67004 \
--testnet-dir ~/.opt/goerli/witti/lighthouse \
--validator all
```
