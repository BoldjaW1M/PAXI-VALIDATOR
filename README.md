# PAXI-VALIDATOR

## Min Spec
32 GB RAM
8 CPU
1 TB SSD

## Installation
```sudo apt update```
```sudo apt install -y docker.io```
```sudo systemctl enable --now docker```
```sudo apt install -y curl```

## Check Ballance
```paxid query bank balances <your_wallet_address>```
Make sure there is a minimum of 1,000,000 upaxi for min self-delegation

## Install Paxi Node via script
```curl -sL https://raw.githubusercontent.com/paxi-web3/paxi/main/scripts/docker_install.sh | bash```

## Run Node
docker run -d --name paxi-node-1 --restart unless-stopped \
  -v "$HOME/paxid/paxi:/root/paxi" \
  --network=host \
  paxi-node \
  ./paxid start

## Go to Toolbox Container
docker run --rm -it --network host \
  -v "$HOME/paxid/paxi:/root/paxi" \
  paxi-node bash

## Wallet Management
Cek ballance
```./paxid keys show <your_key_name>```
```./paxid query bank balances <your_address>```

Import seed phrase
```./paxid keys add <your_key_name> --recover```

## Download genesis.json
```curl -O https://mainnet-rpc.paxinet.io/genesis```

## Set Persistent Peers
Change config (persistent_peers)
```d411fc096e0d946bbd2bdea34f0f9da928c1a714@139.99.68.32:26656,7299b10c0a1545f50c1911b188c579a5e8c5072f@139.99.68.235:26656,...```

## WASM CONTRACT DEPLOY (for DAPPS)
```curl -sL https://raw.githubusercontent.com/paxi-web3/paxi/main/scripts/sync_wasm.sh | bash```

## Create file validator.json
Fill in with detail like :
moniker
pubkey validator
Etc.

## Staking

./paxid tx staking create-validator \
  "/root/paxi/validator.json" \
  --from <your_wallet_name_or_address> \
  --fees 10000upaxi \
  --gas auto

## DONE!!!

