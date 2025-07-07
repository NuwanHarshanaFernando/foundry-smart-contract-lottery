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

Go to https://faucets.chain.link/sepolia and get 25 test LINK

Go to https://docs.chain.link/
Go to Link Token Contracts
Go to Sepolia Testnet
Copy the address

Create another contract called FundSubscription in Interactions.s.sol for fund subscription programatically

Set link in NetworkConfig in HelperConfig.s.sol what we get from https://docs.chain.link/resources/link-token-contracts

For localNetworkConfig, we have to set a fake LINK token

https://github.com/Cyfrin/foundry-smart-contract-lottery-cu/blob/main/test/mocks/LinkToken.sol

Copy the source code

Create a new folder called mocks inside test folder
Create a new file called LinkToken.sol and paste there.

## Solmate to import ERC20 

Go to https://github.com/transmissions11/solmate

```shell
$ forge install transmissions11/solmate@v6 --no-commit
```

Then update remapping in foundry.toml

```shell
$ cast wallet import myaccount --interactive
```

```shell
$ forge script script/Interactions.s.sol:FundSubscription --rpc-url $SEPOLIA_RPC_URL --account default --broadcast
```

## Add Consumer
Create a new contract called AddConsumer in Interactions.s.sol

Go to https://vrf.chain.link/sepolia/ to add Consumer

Go to broadcast/Interactions.s.sol

Go to https://github.com/Cyfrin/foundry-devops

```shell
forge install Cyfrin/foundry-devops
```

```shell
 forge install foundry-rs/forge-std@v1.8.2 
```
Update foundry.toml

fs_permissions = [
    { access = "read", path = "./broadcast" },
    { access = "read", path = "./reports" },
]

Foundry read access to the broadcast folder
Foundry read access to the reports folder

The previous version of Foundry has "ffi = true"

Now testDontAllowPlayersToEnterWhileRaffleIsCalculating is passed because now we have a subcriptionId and a consumer

## Get a Coverage Report
It shows the lines to be tested.

```shell
 forge coverage --report debug
```

To pipe the coverage report to a txt file

```shell
 forge coverage --report debug > coverage.txt
```

