# Full node


In order to sync Chavinci blockchain you must setup full node. This guide describes setup process and some concepts like intraction with your node via command line interface.

## What Is A Full Node?

A full node is a program that fully validates transactions and blocks.
Almost all full nodes also help the network by accepting transactions
and blocks from other full nodes, validating those transactions and
blocks, and then relaying them to further full nodes.

Most full nodes also serve lightweight clients by allowing them to
transmit their transactions to the network and by notifying them when a
transaction affects their wallet. If not enough nodes perform this
function, clients won't be able to connect through the peer-to-peer
network---they'll have to use centralized services instead.

Many people and organizations volunteer to run full nodes using spare
computing and bandwidth resources---but more volunteers are needed to
allow Bitcoin to continue to grow.  This document describes how you can
help and what helping will cost you.



## Getting started

Chavinci software runs on all operating systems: Linux, macOS and Windows. You can get latest binaries from [GitHub](github.com/ChavinciChain/ChavinciChain/releases/latest) or build it on your own using code from [master](https://github.com/ChavinciChain/ChavinciChain/tree/master) branch.

Once you downloaded (or compiled) binaries at your machine, you will have this two binaries:

 - `./chad` - headless Chavinci daemon responsible for syncing blockchain and providing wallet service
 - `./cha-cli` - command line client which allows interact with Chavinci node and wallet

## Configuration

You can specify node params in `chachain.conf` file at `.chachain` folder (or `C:\Users\Username\AppData\Roaming\ChavinciChain` on Windows).

Example config file looks like this:

```
rpcuser=nodeuser
rpcpassword=supersecurepassword
daemon=1
``` 

## Running node

Running Chavinci node pretty straightforward, you can use `-printtoconsole` flag to see the output or use `-daemon` to run it in headless daemon mode. This flags can also be specified in config file instead.

```
./Chavincichaind -daemon
```

## Stopping node

If you launched Chavinci node in daemon mode, it can be stopped using cli utility like this:

```
Chavincichain-cli stop
```


## Chavinci Console RPC Functions

Here are some common Chavinci RPC functions you can use with Chavinci-core or a similar module:

- `getblockchaininfo`: Returns basic information about the Chavinci network.
- `getblock blockhash`: Retrieves information about a specific block.
- `gettransaction txid`: Retrieves information about a specific transaction.
- `getbalance [account], [minconf], [include_watchonly] `: Retrieves the balance of a specific account or all accounts.
- `listtransactions  [account], [count], [skip], [include_watchonly] `: Lists the transaction history of a specific account or all accounts.
- `sendtoaddress  address, amount, [comment], [comment_to], [subtractfeefromamount], [replaceable], [conf_target], [estimate_mode] `: Sends Chavinci to a specific address.
- `listunspent [minconf], [maxconf], [addresses] `: Lists unspent transactions.
- `listreceivedbyaddress [minconf], [include_empty], [include_watchonly] `: Lists the amount of Chavinci sent to a specific account.
- `createwallet wallet_name, [disable_private_keys], [blank], [passphrase] `: Creates a new Chavinci wallet.
- `getnewaddress [account] `: Generates a new Chavinci address.
- `listwallets`: Lists the wallets on the Chavinci node.
- `encryptwallet passphrase `: Encrypts the wallet.
- `backupwallet destination `: Backs up the wallet.
- `importaddress address, [label], [rescan], [p2sh] `: Imports an external Chavinci address.
- `importprivkey privkey, [label], [rescan] `: Imports a private key.
- `sendmany from_account, to_addresses, [minconf], [comment], [subtractfeefrom] `: Sends Chavinci to multiple addresses.
- `generatetoaddress blocks, address, [maxtries] `: Generates blocks to a specific address for the test network.


## Chavinci Node.js Client

The Node.js client for Chavinci Core or a similar Chavinci node supports a variety of Remote Procedure Call (RPC) functions. Here are some common Chavinci RPC functions you can use with Chavinci-core or a similar module:

- `getBlockchainInfo()`: Returns basic information about the Chavinci network.
- `getBlock(blockhash)`: Retrieves information about a specific block.
- `getTransaction(txid)`: Retrieves information about a specific transaction.
- `getBalance([account], [minconf], [include_watchonly])`: Retrieves the balance of a specific account or all accounts.
- `listTransactions([account], [count], [skip], [include_watchonly])`: Lists the transaction history of a specific account or all accounts.
- `sendToAddress(address, amount, [comment], [comment_to], [subtractfeefromamount], [replaceable], [conf_target], [estimate_mode])`: Sends Chavinci to a specific address.
- `listUnspent([minconf], [maxconf], [addresses])`: Lists unspent transactions.
- `listReceivedByAddress([minconf], [include_empty], [include_watchonly])`: Lists the amount of Chavinci sent to a specific account.
- `createWallet(wallet_name, [disable_private_keys], [blank], [passphrase])`: Creates a new Chavinci wallet.
- `getNewAddress([account])`: Generates a new Chavinci address.
- `listWallets()`: Lists the wallets on the Chavinci node.
- `encryptWallet(passphrase)`: Encrypts the wallet.
- `backupWallet(destination)`: Backs up the wallet.
- `importAddress(address, [label], [rescan], [p2sh])`: Imports an external Chavinci address.
- `importPrivKey(privkey, [label], [rescan])`: Imports a private key.
- `sendMany(from_account, to_addresses, [minconf], [comment], [subtractfeefrom])`: Sends Chavinci to multiple addresses.
- `generateToAddress(blocks, address, [maxtries])`: Generates blocks to a specific address for the test network.

These are just a few examples of RPC functions, and Chavinci Core or other Chavinci nodes support many more. Refer to the documentation of the client library you are using to find and utilize the specific functions you need.