## **Prerequisites**

* Rust 1.76+
* Cargo
* [Wallet-contract](./create-giver.md) to be used as a giver with keys
* Contract, for example: [`helloWorld.sol`](./create-and-compile-contract.md)
* [Demo application](https://github.com/gosh-sh/gosh-examples/tree/main/sdk/rust/helloWorld)


**This demo app implements the following logic:**

1. Creates and initialize an instance of the SDK client;

2. Creates a giver contract instance (will be used for send tokens to helloWorld contract);

3. Deploys the helloWorld contract:

    3.1 Generates key pair for the contract;

    3.2 Calculate future address of the contract;

    3.3 Sends to the future address of the contract some tokens required for deploy;

    3.4 Returns instance of the helloWorld contract;

4. Calls some methods (getter and setter) of the contract.


!!! warning "Important"

    **After you have created and deployed the `wallet` and `helloWorld` contracts, you should to place their `ABI files` in the `resources` folder.**

!!! info

    To replenish the balance of wallet-contract, please contact us in [Channel on Telegram](https://t.me/+1tWNH2okaPthMWU0).

## **Setup giver**

Before you start, you should setup a wallet-contract to be used as a giver.  
Edit `.env` file with following content:

```
CONTRACT_CODE=PATH_TO_HELLOWORLD_CONTRACT_CODE    # helloWorld.tvc
GIVER_ADDRESS=YOUR_WALLET_ADDRESS
GIVER_KEYS=PATH_TO_YOUR_WALLET_KEYS_FILE
```

## **Run it**

```sh
cargo run
```

You will see a result similar to the following:
```
Future address: 0:41b8b9d954bfd2c9646fd3e6fc56c73cc091fd5acbcee6b1c2593b4d8beecddf
Requesting tokens from giver-contract...
Transaction id: 9167ef30059487d8dbfbd3e505d3fa3944218a748b9f8bc9a5344983555da377

Contract status: Uninit (ready to deploy)
Contract balance: 1000000000 nanotokens
Contract has been deployed
Timestamp result[1]: 1710358282
Updating timestamp...
Timestamp result[2]: 1710358284
```

## **Source code**

The source code of all the components used can be found [here](https://github.com/gosh-sh/gosh-examples)