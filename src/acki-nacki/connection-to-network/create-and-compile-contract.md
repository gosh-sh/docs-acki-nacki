## **Prerequisites**

* [Solidity Compiler](https://github.com/gosh-sh/TON-Solidity-Compiler)  

## **Install Solidity compiler**

Download and install the Solidity compiler for required platform from [here](https://github.com/gosh-sh/TON-Solidity-Compiler/releases)

## **Create contract**

Create file `helloWorld.sol` with following content:

```solidity
pragma ton-solidity >= 0.35.0;
pragma AbiHeader expire;

// This is class that describes you smart contract.
contract helloWorld {
    // Contract can have an instance variables.
    // In this example instance variable `timestamp` is used to store the time of `constructor` or `touch`
    // function call
    uint32 public timestamp;

    // Contract can have a `constructor` – function that will be called when contract will be deployed to the blockchain.
    // In this example constructor adds current time to the instance variable.
    // All contracts need call tvm.accept(); for succeeded deploy
    constructor() public {
        // Check that contract's public key is set
        require(tvm.pubkey() != 0, 101);
        // Check that message has signature (msg.pubkey() is not zero) and
        // message is signed with the owner's private key
        require(msg.pubkey() == tvm.pubkey(), 102);
        // The current smart contract agrees to buy some gas to finish the
        // current transaction. This actions required to process external
        // messages, which bring no value (hence no gas) with themselves.
        tvm.accept();

        timestamp = block.timestamp;
    }

    function renderHelloWorld () public pure returns (string) {
        return 'helloWorld';
    }

    // Updates variable `timestamp` with current blockchain time.
    function touch() external {
        // Each function that accepts external message must check that
        // message is correctly signed.
        require(msg.pubkey() == tvm.pubkey(), 102);
        // Tells to the TVM that we accept this message.
        tvm.accept();
        // Update timestamp
        timestamp = block.timestamp;
    }

    function sendValue(address dest, uint128 amount, bool bounce) public view {
        require(msg.pubkey() == tvm.pubkey(), 102);
        tvm.accept();
        // It allows to make a transfer with arbitrary settings
        dest.transfer(amount, bounce, 0);
    }
}
```

**Full TVM Solidity API reference is** [here](https://github.com/gosh-sh/TON-Solidity-Compiler/blob/master/API.md)

## **Compiling**

Compile the contract using Solidity compiler:

```shell
sold helloWorld.sol
```

The compiler produces `helloWorld.code`, `helloWorld.tvc` and `helloWorld.abi.json` to be used in the following steps.

Binary code of your contract is recorded into `helloWorld.tvc` file.

## **Source code**

You can find full source code of this contract and its artifacts [here](https://github.com/gosh-sh/gosh-examples/tree/main/contracts/helloWorld)
