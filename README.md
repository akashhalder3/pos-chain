# Run a node and (optionally) stake ETH using Prysm

### configuration:
Operating system: Linux
Network: Private
Execution client: Geth
EN-BN connection: HTTP-JWT

### Introduction:

This configuration uses Prysm as a consensus client and go-ethereum for execution.It starts from proof-of-stake and does not go through the Ethereum merge.This sets up a single node development network with 64 deterministically-generated validator keys to drive the creation of blocks in an Ethereum proof-of-stake chain. 

At a high level, we'll walk through the following flow:
1. Configure an execution node using an execution-layer client.
2. Configure a beacon node using Prysm, a consensus-layer client.
3. Configure a validator client and stake ETH using Prysm.


### Review prerequisites and best practices:
#### Type
Execution + Beacon
#### Benefits
Contributes to the security of Ethereum's ecosystem. Lets you access the network directly without having to trust a third party service.