# Chavinci Console RPC Functions

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

