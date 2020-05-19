run teku on witti testnet

```
teku \
--config-file="/home/user/.opt/goerli/witti/teku/config.yaml" \
--network="/home/user/.opt/goerli/witti/teku/chain.yaml"
```

generate keypairs and make deposits

```
teku validator generate \
--network="/home/user/.opt/goerli/witti/teku/chain.yaml" \
--eth1-endpoint="http://127.0.0.1:8545" \
--eth1-deposit-contract-address="0x6225f431644Ecf8A30b672D42b77c28297542b13" \
--eth1-keystore-file="/home/user/.ethereum/goerli/keystore/UTC--2020-01-18T11-33-11.045251948Z--272dd1ff68461dfa848c9c30d8e2c3180a8f18de" \
--eth1-keystore-password-file="/home/user/.opt/goerli/witti/password.txt" \
--keys-output-path="/home/user/.local/share/teku/keystore" \
--encrypted-keystore-validator-password-file="/home/user/.opt/goerli/witti/password.txt" \
--encrypted-keystore-withdrawal-password-file="/home/user/.opt/goerli/witti/password.txt" \
--number-of-validators=32
```

restart teku with validators enabled

```
teku \
--config-file="/home/user/.opt/goerli/witti/teku/config.yaml" \
--network="/home/user/.opt/goerli/witti/teku/chain.yaml"
```

(see config for validator key/pass)