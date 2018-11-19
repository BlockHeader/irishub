# How To Participate in Genesis Process

## Requirements

You must have follow this [guide](Install-Iris.md) to install the correct version of **Iris**.

## Gentx

Please run the `keys add` subcommand and run the `gen-tx` subcommand to generate files.


```
iriscli keys add your_name
iris gentx --name=your_name --home=<path_to_home> --ip=Your_public_IP
```

For example,

```
iriscli keys add alice
iris gentx --name=alice --home=iris --chain-id=irishub-stage --ip=1.1.1.1
```

There will be a gentx-node-ID.json a file at `$IRISHOME/config/gentx/`.

The content of the file will be:

```
{
  "type": "auth/StdTx",
  "value": {
    "msg": [
      {
        "type": "cosmos-sdk/MsgCreateValidator",
        "value": {
          "Description": {
            "moniker": "chenggedexiaokeai.local",
            "identity": "",
            "website": "",
            "details": ""
          },
          "Commission": {
            "rate": "0.1000000000",
            "max_rate": "0.2000000000",
            "max_change_rate": "0.0100000000"
          },
          "delegator_address": "faa1cf25tf4pfjdhkzx8lqnkajlse6jcpm2fyw4yme",
          "validator_address": "fva1cf25tf4pfjdhkzx8lqnkajlse6jcpm2f3lltx7",
          "pubkey": {
            "type": "tendermint/PubKeyEd25519",
            "value": "/JvLFsvyMgm2ND4QgN4JKyLxhL42dVgat67383Q+mPY="
          },
          "delegation": {
            "denom": "iris-atto",
            "amount": "100000000000000000000"
          }
        }
      }
    ],
    "fee": {
      "amount": null,
      "gas": "200000"
    },
    "signatures": [
      {
        "pub_key": {
          "type": "tendermint/PubKeySecp256k1",
          "value": "AtfNRj0zYvffAQG+iad6SScfdl29ag9G3EI0JDSwKJmy"
        },
        "signature": "BwTejBceK4M+3LzmNl62jVFUr9wVv//UO7iI/yWi5KFoez9eY43HSlaZJf+3rnKLjosn2tD79EIw55BJ6SbYzQ==",
        "account_number": "0",
        "sequence": "0"
      }
    ],
    "memo": "0eb02fdabb96923ac1e855ac012a5a624793264a@1.1.1.1:26656"
  }
}
```
This is the `CreateValidator` message.
validator is generated by \$IRISHOME/config/priv_validator.json

## Submit Gentx

Submit your `gentx-<node-id>.json` to `https://github.com/irisnet/testnets/tree/master/fuxi/fuxi-4000/config/gen-tx/` by createing a pull request.

After the team has collected all the gen-tx transactions, we will publish the genesis file in the following folder: `https://github.com/irisnet/testnets/tree/master/testnets/fuxi-3001/config/`

You could then download the final genesis file and start a node. 
