# PrateekCoin
A simple blockchain application development


<p align="center">
  <a href="" rel="noopener">
 <img width=200px height=200px src="https://i.imgur.com/VELRxXl.png" alt="Project logo"></a>
</p>

<h3 align="center"> PrateekCoin </h3>

---

*⚠️ For education purposes only. This is by no means a complete implementation and it is by no means secure!*

## Developed BlockChain with this Features :- 

* Simple proof-of-work algorithm
* Verify blockchain (to prevent tampering)
* Generate wallet (private/public key)
* Sign transactions

## 🏁 Getting Started <a name = "getting_started"></a>

### Install library
```
npm install --save savjeecoin
```

### Generate a keypair
To make transactions on this blockchain you need a keypair. The public key becomes your wallet address and the private key is used to sign transactions.

```js
const EC = require('elliptic').ec;
const ec = new EC('secp256k1');

const myKey = ec.genKeyPair();
```

The `myKey` object now contains your public & private key:

```js
console.log('Public key:', myKey.getPublic('hex'));
console.log('Private key:', myKey.getPrivate('hex'));
```

### Create a blockchain instance
Now you can create a new instance of a Blockchain:

```js
const {Blockchain, Transaction} = require('savjeecoin');

const myChain = new Blockchain();
```

### Adding transactions
```js
// Transfer 100 coins from my wallet to "toAddress"
const tx = new Transaction(myKey.getPublic('hex'), 'toAddress', 100);
tx.signTransaction(myKey);

myChain.addTransaction(tx);
```

To finalize this transaction, we have to mine a new block. We give this method our wallet address because we will receive a mining reward:

```js
myChain.minePendingTransactions(myKey.getPublic('hex'));
```


---

* node_modules :- [npm install --save crypto-js] 
* Proof_Of_Work :- It will secure our blockchain against spammers and people trying to tamper with our blocks.
