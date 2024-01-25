# Run a proof of stake node using geth and Prysm

### Configuration:
Operating system: Linux \
Network: Private \
Execution client: Geth \
EN-BN connection: HTTP-JWT

### Introduction:

This configuration uses Prysm as a consensus client and go-ethereum for execution. It starts from proof-of-stake and does not go through the Ethereum merge. This sets up a single node development network with 64 deterministically-generated validator keys to drive the creation of blocks in an Ethereum proof-of-stake chain. 

At a high level, we'll walk through the following flow:
1. Configure an execution node using an execution-layer client.
2. Configure a beacon node using Prysm, a consensus-layer client.
3. Configure a validator client and stake ETH using Prysm.


### Review prerequisites and best practices:
#### Type
1. Execution + Beacon
    #### Benefits
    Contributes to the security of the ecosystem. Lets you access the network directly without having to trust a third party service.
    #### Requirements
    1. Software
        * Execution node client, beacon node client 
    2. OS 
        * 64-bit Linux
    3. CPU
        * 4+ cores @ 2.8+ GHz
    4. Memory
        * 4GB+ RAM
    5. Storage
        * SSD with at least 10GB free space
    6. Network
        * 8 MBit/sec broadband

2. Validator
    #### Benefits
    Lets you stake ETH, propose + validate blocks, earn staking rewards + transaction fee tips.
    #### Requirements
    1. Everything above, plus...
    2. Software
        * Validator client, browser-based crypto wallet
    3. Hardware 
        * A new machine that has never been connected to the internet that you can use to securely generate your mnemonic phrase and keypair
    4. 32 ETH

## Install GCC compiler
```
    sudo apt update
    sudo apt install build-essential
```

### Go Installation
```
    sudo rm -rf /usr/local/go && wget https://go.dev/dl/go1.21.6.linux-amd64.tar.gz
    sudo tar -C /usr/local -xzf go1.21.6.linux-amd64.tar.gz
    export PATH=$PATH:/usr/local/go/bin
    go version
```

### Install Prysm
```
    git clone https://github.com/prysmaticlabs/prysm && cd prysm
    go build -o=../beacon-chain ./cmd/beacon-chain
    go build -o=../validator ./cmd/validator
    go build -o=../prysmctl ./cmd/prysmctl
    cd ..
```

### Install Geth

### Clone the repo
```
    git clone https://github.com/akashhalder3/pos-chain.git && cd pos-chain
```

### Service files command
```
    sudo systemctl daemon-reload
    sudo systemctl start beacon-chain.service
    sudo journalctl -u beacon-chain.service -f
    sudo systemctl stop beacon-chain.service

    sudo systemctl start pos-geth.service
    sudo journalctl -u pos-geth.service -f
    sudo systemctl stop pos-geth.service

    sudo systemctl start pos-validator.service
    sudo journalctl -u pos-validator.service -f
    sudo systemctl stop pos-validator.service
```






