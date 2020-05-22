run beacon node

```
lighthouse bn --http \
--testnet-dir ~/.opt/goerli/witti/lighthouse \
--eth1-endpoint http://127.0.0.1:9779
```

create hd wallet

```
lighthouse account_manager wallet create \
--name "witti" \
--passphrase-file ~/.opt/goerli/witti/password.txt \
--testnet-dir ~/.opt/goerli/witti/lighthouse \
--mnemonic-output-path ~/.opt/goerli/witti/mnemonic.txt
```

create validator keypairs

```
lighthouse account_manager validator create \
--at-most 2 \
--testnet-dir ~/.opt/goerli/witti/lighthouse \
--wallet-name "witti" \
--wallet-passphrase ~/.opt/goerli/witti/password.txt
```

make validator deposits

unlock account first

```
lighthouse account_manager validator deposit \
--eth1-ipc ~/.ethereum/goerli/geth.ipc \
--from-address 04f67c6fa446486d8da0a3534566bdc75ef67004 \
--testnet-dir ~/.opt/goerli/witti/lighthouse \
--validator all
```

run validator

```
lighthouse vc \
--testnet-dir ~/.opt/goerli/witti/lighthouse
```