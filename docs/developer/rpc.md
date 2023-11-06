# RPC

You can interact with Chavinci node using remote procedure call (RPC). Node will reply with data in JSON format.

## Making request

You can make request to your node via `Chavincichain-cli` or by sending POST request with payload to port `33440`.

Example `Chavincichain-cli` request:

```
./Chavincichain-cli getblock 37eb3f4b73df32d22c4a1c58e91f6e7f0bf58e34e448a8e59d6b2576eeb9c238
```

Example POST request:

```
curl --data-binary '{"jsonrpc":"1.0","id":"curltext","method":"getblock","params":["37eb3f4b73df32d22c4a1c58e91f6e7f0bf58e34e448a8e59d6b2576eeb9c238"]}' -H 'content-type:text/plain;' http://nodeuser:supersecurepassword@127.0.0.1:33440
```

!!! hint
    In order to make RPC request via POST request you must configure `rpcuser` and `rpcpassword` for your node.

## Network

This methods can be used to get general information about the network.

`getblockchaininfo` - returns info about blockchain

```JSON
{
	"chain": "main",
	"blocks": 271823,
	"headers": 271823,
	"bestblockhash": "e4bc6d4b818792a1fb2c57c08454099c4ebf1fcd2f23490573e0260918193b89",
	"difficulty": 0.002555948098984594,
	"mediantime": 1608143056,
	"verificationprogress": 1,
	"chainwork": "0000000000000000000000000000000000000000000001f22354cf302a1790ec",
	"size_on_disk": 417448998,
	"pruned": 0,
	"softforks": [
	],
	"bip9_softforks": {
	},
	"warnings": ""
}
```


`getblockhash <height>` - returns block hash

`0012eb05991b2ee8d074fde6c03089d2517937e28adc4219f0a4742b7805be96`


`getblock <hash>` - returns block information

```JSON
{
	"hash": "0012eb05991b2ee8d074fde6c03089d2517937e28adc4219f0a4742b7805be96",
	"confirmations": 271835,
	"strippedsize": 231,
	"size": 231,
	"weight": 924,
	"height": 1,
	"version": 536870912,
	"versionHex": "20000000",
	"merkleroot": "49f3bbf10c853367aa597d96a0307e8cb7e0e3ddc6e3e668c141143056a48133",
	"tx": [
		"49f3bbf10c853367aa597d96a0307e8cb7e0e3ddc6e3e668c141143056a48133"
	],
	"time": 1589880735,
	"mediantime": 1589880735,
	"nonce": 284,
	"bits": "1f3fffff",
	"difficulty": 2.384149979653205e-07,
	"chainwork": "0000000000000000000000000000000000000000000000000000000000000800",
	"previousblockhash": "000c513d39b0e3657b7b0ca79b2d4b9b18c1f03dacb394acf0e71f49064b3306",
	"nextblockhash": "003c074613108695565ea4e76957a346038ff7aa12ab951af3508398bb9b23fd",
	"flags": "proof-of-work",
	"modifier": "d2ec909dc48208a3a4d92162c14d116b48e27c7cb579f1c3cb4573e1b5c2d4ac"
}
```


## Transactions

This methods can be used to get information about transactions.

`getrawtransaction <hash> <verbose>` - returns information about transaction (set `verbose` to `true` for json output)

```JSON
{
	"txid": "49f3bbf10c853367aa597d96a0307e8cb7e0e3ddc6e3e668c141143056a48133",
	"hash": "49f3bbf10c853367aa597d96a0307e8cb7e0e3ddc6e3e668c141143056a48133",
	"version": 1,
	"timestamp": 1589880735,
	"size": 149,
	"vsize": 149,
	"locktime": 0,
	"vin": [
		{
			"coinbase": "510101",
			"sequence": 4294967295
		}
	],
	"vout": [
		{
			"value": 2100000000,
			"n": 0,
			"scriptPubKey": {
				"asm": "03131079e6248a288fcf9daf9828f09544e3f853e870afc651efdb0ca9298059ab OP_CHECKSIG",
				"hex": "2103131079e6248a288fcf9daf9828f09544e3f853e870afc651efdb0ca9298059abac",
				"reqSigs": 1,
				"type": "pubkey",
				"addresses": [
					"KrbwDveomVrY4fNH5GrHU52A2HqpzgmCkG"
				]
			},
			"spentTxId": "df766dc83db4a93857cb3076bd043ea06138526e282744ad63a478eaa6bb0662",
			"spentIndex": 0,
			"spentHeight": 12,
			"valueSat": 210000000000000000
		},
		{
			"value": 0,
			"n": 1,
			"scriptPubKey": {
				"asm": "OP_RETURN aa21a9ede2f61c3f71d1defd3fa999dfa36953755c690689799962b48bebd836974e8cf9",
				"hex": "6a24aa21a9ede2f61c3f71d1defd3fa999dfa36953755c690689799962b48bebd836974e8cf9",
				"type": "nulldata"
			},
			"valueSat": 0
		}
	],
	"hex": "010000009fa7c35e010000000000000000000000000000000000000000000000000000000000000000ffffffff03510101ffffffff020000d52ae311ea02232103131079e6248a288fcf9daf9828f09544e3f853e870afc651efdb0ca9298059abac0000000000000000266a24aa21a9ede2f61c3f71d1defd3fa999dfa36953755c690689799962b48bebd836974e8cf900000000",
	"blockhash": "0012eb05991b2ee8d074fde6c03089d2517937e28adc4219f0a4742b7805be96",
	"height": 1,
	"confirmations": 271841,
	"time": 1589880735,
	"blocktime": 1589880735
}
```


`getchaintxstats` - returns statistics about the total number and rate of transactions in the chain

```JSON
{
	"time": 1608144544,
	"txcount": 1271608,
	"window_block_count": 40500,
	"window_tx_count": 246854,
	"window_interval": 2724352,
	"txrate": 0.09061017078556663
}
```

## Wallet

This methods can be used to get information about wallet.

`getbalance` - returns entite Chavinci balance of your wallet

`0.00000000`


`listmytokens` - returns list of all tokens your wallet is holding

```JSON
{
  "CCA": 984.00000000
}
```


`getnewaddress <label>` - returns new address and assign label if it was set

`KpmtABZnYx2qxJwu4wSmRSsEuJ6NwJFd5S`


`listtransactions <label> <count> <skip>` - returns list of last transactions for given label (use `*` to get list of all incoming transactions)

```JSON
[
	{
		"account": "testlabel",
		"token_type": "transfer_token",
		"token_name": "CCA",
		"amount": 45.48900000,
		"address": "KqFZpfbZ6kFFWqg22jv3cBES8o4cCERmW",
		"vout": 0,
		"category": "receive",
		"blockhash": "3b816b7cb73c98ad22e4673f900eb2f6a9a0a15692227769ab3dc95d301f8ec4",
		"blockindex": 2,
		"blocktime": 1607785696,
		"txid": "cacf4bf3dcc43fbe6a76ff7d9f6b4625cda409538928cc9c89881305db95e5d5",
		"confirmations": 5510,
		"walletconflicts": [
		],
		"time": 1607785660,
		"timereceived": 1607785660
	},
	{
		"account": "testlabel",
		"token_type": "transfer_token",
		"token_name": "CCA",
		"amount": 45.51290000,
		"address": "KqFZpfbZ6kFFWqg22jv3cBES8o4cCERmW",
		"vout": 0,
		"category": "receive",
		"blockhash": "22b5cebcae8a6c3fa3ccf4acd67293ae42b2273e606e97dd9d4be751afa9df9c",
		"blockindex": 2,
		"blocktime": 1607879552,
		"txid": "61f7fcea979aec1a9b8812f36e75589ea2b9d4f3ad168b4e1d2e9a00d6206796",
		"confirmations": 4115,
		"walletconflicts": [
		],
		"time": 1607879552,
		"timereceived": 1607879552
	},
	{
		"account": "testlabel",
		"token_type": "transfer_token",
		"token_name": "CCA",
		"amount": 45.53510000,
		"address": "KqFZpfbZ6kFFWqg22jv3cBES8o4cCERmW",
		"vout": 0,
		"category": "receive",
		"blockhash": "e9f844b193a3e75eb60c95b5ab2db7eb51368307c6fa55cf859bd9a860c0505a",
		"blockindex": 2,
		"blocktime": 1607964192,
		"txid": "d16972d5f1b578e143e9cc93f33cefec8eb52926b588d14e425ba9dceef434a4",
		"confirmations": 2854,
		"walletconflicts": [
		],
		"time": 1607964141,
		"timereceived": 1607964141
	}
]
```

`sendtoaddress <address> <amount> <locktime>` - sends specified amount of Chavinci to address with locktime (if it was set)

`d16972d5f1b578e143e9cc93f33cefec8eb52926b588d14e425ba9dceef434a4`


`sendmany "*" <recepients>` - sends Chavinci to multiple recipients (second argument must be set to `*`). Recepients is regular JSON object with address as a key and amount as value: `{"cud4EpNGfSqecAdB3FH6x6wvNfVEL2iMn": 10}`

```JSON
[
	"cacf4bf3dcc43fbe6a76ff7d9f6b4625cda409538928cc9c89881305db95e5d5"
]
```


`transfer <token> <amount> <address> <locktime>` - sends specified amount of token to address with locktime (if it was set)

```JSON
[
	"7c9f23b4e8c4df8fa044e19cdadfb1be8cf9a1e38687b4e877978a9747f13780"
]
```


`transfermany <token> <recepients>` - sends token to multiple recipients (second argument must be set to `*`). Recepients is regular JSON object with address as a key and amount as value: `{"cud4EpNGfSqecAdB3FH6x6wvNfVEL2iMn": 10}` 

```JSON
[
	"61f7fcea979aec1a9b8812f36e75589ea2b9d4f3ad168b4e1d2e9a00d6206796"
]
```

## Tokens

This methods can be used to create/update tokens and get related token information.

`issue <name> <amount> <address> <change_address> <units> <reissuable>` - issue token to address (if specified)

```JSON
[
	"94cac36a44021ee3e8cdf7365b34212e588679b927858453a714d4fa97df033a"
]
```


`reissue <name> <amount> <address> <change_address> <reissuable> <units>` - reissue token and/or update infromation about it (for example change number of units or reissuability)

```JSON
[
	"0bcd37b40b79608f582a0fb17666f5c639d79acf72e4d5ce25c3726b3f7fea33"
]
```


`listtokens` - returns list of all existing tokens

```JSON
[
	"CCA"
]
```


`gettokendata <token>` - returns information about tocken

```JSON
{
	"name": "CCA",
	"amount": 1000000000.00000000,
	"units": 8,
	"reissuable": 1
}
```


`listtokenbalancesbyaddress <address>` - return all token balances for specified address

```JSON
{
	"CCA": 45731.24990000
}
```


`listaddressesbytoken <token>` - returns list of addresses/balances which hold specified token

```JSON
{
	"cbLnN9J9wuPVzkqeTjzq9efRBSxTHJGh2": 45731.24990000,
	"chEy59XfADWu5LspUvN9KYbaggTb3thmr": 5138.96400000,
	"cmyLEGXAxzHLNEuj8wTiXbCzLR4Uaon79": 10277.92800000,
	"cqDW4apwJi6QsHN3q3h5LMXWw1LgtaWgz": 3.01100000,
	"cqS79DH5SGqrNGjKVDfHQLGCsBxYKMp4j": 25522.00000000,
	"cr1m9cry8yhjUzBLhNxbvQsmqc1u7TaWD": 4079.46780000,
	"crqLZGi82SJdVukvvcTfRpsmkpCx4fX4K": 108874.53530000,
	"cswvLxmJJJCBNoVW3U7YNqLDNS7i9d6bx": 3.00000000,
	"ctUYjQP8BBQwTFgJZebnxoiAqsF11DmXE": 94700.49149998,
	"cud4EpNGfSqecAdB3FH6x6wvNfVEL2iMn": 1.00000000,
	"cvmj3GNV4DE8Ms8yuKMGLHZDc88pr8Gzv": 1000.00000000,
	"cvwTDCqFshmF1Xnqo1yj29TG8GQwyUHg4": 27703.98720000,
	"cwA5otMB4qCzvFiERcBFj6JdaZ2Vvykv7": 1000000.00000000,
	"cwKUUoZUw2DbXu7NWfXKySkSUa9WnRqR6": 12801.75300000,
	"cwufjbDrozt6n5up1vSchveokeoXV9L82": 221074.64239996,
	"cxemToRTChASMY85KSS8rfHHn4YnuEpbJ": 8811.66599998,
	"cxrS24CN53HUkGHzZUybHnqC8hzfBH562": 11.88460509,
	"czEAcXbh2nqBSjSrV3dYFWATrTxvAGcBh": 14.00000000,
	"cX6LWrCX28etVmwdTaWX6X7J8pxBqLgF3u": 38128.91369999,
	"cX6SfVXJMHSF6e3xrzcGkcpSdu9ETBZtzr": 127377.29239999,
	"cX7BYLcxQpt3CANC3KPL8FaLCRDFDQRdCD": 27979.77800000,
	...
}
```