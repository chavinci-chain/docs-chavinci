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

 - `Chavincichaind` - headless Chavinci daemon responsible for syncing blockchain and providing wallet service
 - `Chavincichain-cli` - command line client which allows interact with Chavinci node and wallet

## Configuration

You can specify node params in `Chavincichain.conf` file at `.Chavincichain` folder (or `C:\Users\Username\AppData\Roaming\ChavinciChain` on Windows).

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