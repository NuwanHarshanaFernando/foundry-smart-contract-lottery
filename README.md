## Foundry

**Foundry is a blazing fast, portable and modular toolkit for Ethereum application development written in Rust.**

Foundry consists of:

-   **Forge**: Ethereum testing framework (like Truffle, Hardhat and DappTools).
-   **Cast**: Swiss army knife for interacting with EVM smart contracts, sending transactions and getting chain data.
-   **Anvil**: Local Ethereum node, akin to Ganache, Hardhat Network.
-   **Chisel**: Fast, utilitarian, and verbose solidity REPL.

## Documentation

https://book.getfoundry.sh/

## Usage

### Build

```shell
$ forge build
```

### Test

```shell
$ forge test
```

### Format

```shell
$ forge fmt
```

### Gas Snapshots

```shell
$ forge snapshot
```

### Anvil

```shell
$ anvil
```

### Deploy

```shell
$ forge script script/Counter.s.sol:CounterScript --rpc-url <your_rpc_url> --private-key <your_private_key>
```

### Cast

```shell
$ cast <subcommand>
```

### Help

```shell
$ forge --help
$ anvil --help
$ cast --help
```

### Install from the github

```shell
$ forge install smartcontractkit/chainlink-brownie-contracts@1.1.1
```

### To Format 

```shell
$ forge fmt
```
## Tests

1. Write deploy scripts
    1. Note, these will not work on zkSync
2. Write tests
    1. Local chain
    2. Forked testnet
    3. Forked mainnet

    Create a file called DeployRaffle.s.sol inside script folder

    Create a file called HelperConfig.s.sol insdide script folder

    Get VRF Coordinator of Sepolia Testnet

    https://docs.chain.link/vrf/v2-5/supported-networks

    Copy the VRF Coordinator of Ethereum Sepolia Testnet and paste for value of vrfCoordinator
    in HelperConfig.s.sol
    0x9DdfaCa8183c41ad55329BdeeD9F6A8d53168B1B

    Check the constructor of VRFCoordinatorV2_5Mock

    //constructor(uint96 _baseFee, uint96 _gasPrice, int256 _weiPerUnitLink) SubscriptionAPI() {}

## Testing Start

Create unit and integration folders inside test folder

## Headers (Optional)

https://github.com/transmissions11/headers

```shell
$ forge test --mt testRaffleRevertsWhenYouDontPayEnough
```

## Create Subscription Id
Create a script called Interactions.s.sol

Go to https://vrf.chain.link/sepolia/ to create Subscription

```shell
$ cast sig createSubscription 0xa21a23e4
```

## To get the value of signatures from openchain database (get the function from hexdata)
https://openchain.xyz/signatures





