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
--eth1-endpoint="http://127.0.0.1:9779" \
--eth1-deposit-contract-address="0x9eED6A5741e3D071d70817beD551D0078e9a2706" \
--eth1-keystore-file="/home/user/.ethereum/goerli/keystore/UTC--2020-04-23T06-29-02.894097316Z--04f67c6fa446486d8da0a3534566bdc75ef67004" \
--eth1-keystore-password-file="/home/user/.opt/goerli/witti/password.txt" \
--keys-output-path="/home/user/.local/share/teku/keystore" \
--encrypted-keystore-validator-password-file="/home/user/.opt/goerli/witti/password.txt" \
--encrypted-keystore-withdrawal-password-file="/home/user/.opt/goerli/witti/password.txt" \
--number-of-validators=2
```

restart teku with validators enabled

(make sure to add validator paths and passwords to the config.yaml)

```
teku \
--config-file="/home/user/.opt/goerli/witti/teku/config.yaml" \
--network="/home/user/.opt/goerli/witti/teku/chain.yaml"
```

(see config for validator key/pass)