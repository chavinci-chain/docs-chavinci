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

Chavinci software runs on all operating systems: Linux, macOS and Windows. You can get latest binaries from <a href="https://github.com/chavinci-chain/chavinci-releases/releases" target="_blank" style="color: #526cfe; ">GitHub</a>  or build it on your own using code from [master](https://github.com/ChavinciChain/ChavinciChain/tree/master) branch.

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
./chad -daemon
```

## Stopping node

If you launched Chavinci node in daemon mode, it can be stopped using cli utility like this:

```
./cha-cli stop
```
or

```
pkill -9 chad
```


## Chavinci Console RPC Functions

Here are some common Chavinci RPC functions you can use with Chavinci-core or a similar module:

1- Returns basic information about the Chavinci network:
```
./cha-cli getblockchaininfo
```

2- Retrieves information about a specific block:
```
./cha-cli getblock :blockhash
```

3- Retrieves information about a specific transaction:
```
./cha-cli gettransaction :txid
```

4- Retrieves the balance of a specific account or all accounts:
```
./cha-cli getbalance [account], [minconf], [include_watchonly] 
```
5- Lists the transaction history of a specific account or all accounts:
```
./cha-cli listtransactions  [account], [count], [skip], [include_watchonly] 
```
6- Sends Chavinci to a specific address:
```
./cha-cli sendtoaddress  address, amount, [comment], [comment_to], [subtractfeefromamount], [replaceable], [conf_target], [estimate_mode] 
```
7- Lists unspent transactions:
```
./cha-cli listunspent [minconf], [maxconf], [addresses]
```
8- Lists the amount of Chavinci sent to a specific account:
```
./cha-cli listreceivedbyaddress [minconf], [include_empty], [include_watchonly]
```
9- Creates a new Chavinci wallet:
```
./cha-cli createwallet wallet_name, [disable_private_keys], [blank], [passphrase]
```
10- Generates a new Chavinci address:
```
./cha-cli getnewaddress [account]
``` 
11- Lists the wallets on the Chavinci node:
```
./cha-cli listwallets
```
12- Encrypts the wallet:
```
./cha-cli encryptwallet passphrase
```
13- Backs up the wallet:
```
./cha-cli backupwallet destination
```
14- Imports an external Chavinci address:
```
./cha-cli importaddress address, [label], [rescan], [p2sh]
```
15- Imports a private key:
```
./cha-cli importprivkey privkey, [label], [rescan]
```
16- Sends Chavinci to multiple addresses:
```
./cha-cli sendmany from_account, to_addresses, [minconf], [comment], [subtractfeefrom]
```
17-  Generates blocks to a specific address for the test network:
```
./cha-cli generatetoaddress blocks, address, [maxtries]
```

