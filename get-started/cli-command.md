# CLI Command

This section details the present commands, command flags in the EVMBuilder Edge, and how they're used.

**JSON OUTPUT SUPPORT**

The `--json` flag is supported on some commands. This flag instructs the command to print the output in JSON format

#### Startup Commands <a href="#startup-commands" id="startup-commands"></a>

| **Command** | **Description**                                                                                                                                                 |
| ----------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| server      | The default command that starts the blockchain client, by bootstrapping all modules together                                                                    |
| genesis     | Generates a _genesis.json_ file, which is used to set a predefined chain state before starting the client. The structure of the genesis file is described below |

**server flags**

_**seal**_

SyntaxExample

`server [--seal SHOULD_SEAL]`

Sets the flag indicating that the client should seal blocks. Default: `true`.

***

_**data-dir**_

SyntaxExample

server \[--data-dir DATA\_DIRECTORY]

Used to specify the data directory used for storing EVMBuilder Edge client data. Default: `./test-chain`.

***

_**jsonrpc**_

SyntaxExample

server \[--jsonrpc JSONRPC\_ADDRESS]

Sets the address and port for the JSON-RPC service `address:port`. If only port is defined `:10001` it will bind to all interfaces `0.0.0.0:10001`. If omitted the service will bind to the default `address:port`. Default address: `0.0.0.0:8545`.

***

_**grpc**_

SyntaxExample

server \[--grpc-address GRPC\_ADDRESS]

Sets the address and port for the gRPC service `address:port`. Default address: `127.0.0.1:9632`.

***

_**libp2p**_

SyntaxExample

server \[--libp2p LIBP2P\_ADDRESS]

Sets the address and port for the libp2p service `address:port`. Default address: `127.0.0.1:1478`.

***

_**prometheus**_

SyntaxExample

server \[--prometheus PROMETHEUS\_ADDRESS]

Sets the address and port for the prometheus server `address:port`. If only port is defined `:5001` the service will bind to all interfaces `0.0.0.0:5001`. If omitted the service will not be started.

***

_**block-gas-target**_

SyntaxExample

server \[--block-gas-target BLOCK\_GAS\_TARGET]

Sets the target block gas limit for the chain. Default (not enforced): `0`.

A more detailed explanation on the block gas target can be found in the TxPool section.

***

_**max-peers**_

SyntaxExample

server \[--max-peers PEER\_COUNT]

Sets the client's maximum peer count. Default: `40`.

Peer limit should be specified either by using `max-peers` or `max-inbound/outbound-peers` flag.

***

_**max-inbound-peers**_

SyntaxExample

server \[--max-inbound-peers PEER\_COUNT]

Sets the client's maximum inbound peer count. If `max-peers` is set, max-inbound-peer limit is calculated using the following formulae.

`max-inbound-peer = InboundRatio * max-peers`, where `InboundRatio` is `0.8`.

***

_**max-outbound-peers**_

SyntaxExample

server \[--max-outbound-peers PEER\_COUNT]

Sets the client's maximum outbound peer count. If `max-peers` is set, max-outbound-peer count is calculated using the following formulae.

`max-outbound-peer = OutboundRatio * max-peers`, where `OutboundRatio` is `0.2`.

***

_**log-level**_

SyntaxExample

server \[--log-level LOG\_LEVEL]

Sets the log level for console output. Default: `INFO`.

***

_**log-to**_

SyntaxExample

server \[--log-to LOG\_FILE]

Defines log file name that will hold all log output from the server command. By default, all server logs will be outputted to console (stdout), but if the flag is set, there will be no output to the console when running server command.

***

_**chain**_

SyntaxExample

server \[--chain GENESIS\_FILE]

Specifies the genesis file used for starting the chain. Default: `./genesis.json`.

***

_**join**_

SyntaxExample

server \[--join JOIN\_ADDRESS]

Specifies the address of the peer that should be joined.

***

_**nat**_

SyntaxExample

server \[--nat NAT\_ADDRESS]

Sets the external IP address without the port, as it can be seen by peers.

***

_**dns**_

SyntaxExample

server \[--dns DNS\_ADDRESS]

Sets the host DNS address. This can be used to advertise an external DNS. Supports `dns`,`dns4`,`dns6`.

***

_**price-limit**_

SyntaxExample

server \[--price-limit PRICE\_LIMIT]

Sets minimum gas price limit to enforce for acceptance into the pool. Default: `1`.

***

_**max-slots**_

SyntaxExample

server \[--max-slots MAX\_SLOTS]

Sets maximum slots in the pool. Default: `4096`.

***

_**config**_

SyntaxExample

server \[--config CLI\_CONFIG\_PATH]

Specifies the path to the CLI config. Supports `.json`.

***

_**secrets-config**_

SyntaxSecond Tab

server \[--secrets-config SECRETS\_CONFIG]

Sets the path to the SecretsManager config file. Used for Hashicorp Vault, AWS SSM and GCP Secrets Manager. If omitted, the local FS secrets manager is used.

***

_**dev**_

SyntaxExample

server \[--dev DEV\_MODE]

Sets the client to dev mode. Default: `false`.

***

_**dev-interval**_

SyntaxExample

server \[--dev-interval DEV\_INTERVAL]

Sets the client's dev notification interval in seconds. Default: `0`.

***

_**no-discover**_

SyntaxExample

server \[--no-discover NO\_DISCOVER]

Prevents the client from discovering other peers. Default: `false`.

***

_**restore**_

SyntaxExample

server \[--restore RESTORE]

Restore blocks from the specified archive file

***

_**block-time**_

SyntaxExample

server \[--block-time BLOCK\_TIME]

Sets block production time in seconds. Default: `2`

***

_**ibft-base-timeout**_

SyntaxExample

server \[--ibft-base-timeout IBFT\_BASE\_TIMEOUT]

Sets the base value of timeout on IBFT consensus. IBFT consensus timeout is calculated by `BaseTimeout + 2^(round)`, or `BaseTimeout * 30` where round exceeds 8. It needs to be larger than block time and `BlockTime * 5` is set if it's not specified.

***

_**access-control-allow-origins**_

SyntaxExample

server \[--access-control-allow-origins ACCESS\_CONTROL\_ALLOW\_ORIGINS]

Sets the authorized domains to be able to share responses from JSON-RPC requests. Add multiple flags `--access-control-allow-origins "https://example1.com" --access-control-allow-origins "https://example2.com"` to authorize multiple domains. If omitted Access-Control-Allow-Origins header will be set to `*` and all domains will be authorized.

***

**genesis flags**

_**dir**_

SyntaxExample

genesis \[--dir DIRECTORY]

Sets the directory for the EVMBuilder Edge genesis data. Default: `./genesis.json`.

***

_**name**_

SyntaxExample

genesis \[--name NAME]

Sets the name for the chain. Default: `polyton-edge`.

***

_**pos**_

SyntaxExample

genesis \[--pos IS\_POS]

Sets the flag indicating that the client should use Proof of Stake IBFT. Defaults to Proof of Authority if flag is not provided or `false`.

***

_**epoch-size**_

SyntaxExample

genesis \[--epoch-size EPOCH\_SIZE]

Sets the epoch size for the chain. Default `100000`.

***

_**premine**_

SyntaxExample

genesis \[--premine ADDRESS:VALUE]

Sets the premined accounts and balances in the format `address:amount`. The amount can be in either decimal or hex. Default premined balance: `0x3635C9ADC5DEA00000`.

***

_**chainid**_

SyntaxExample

genesis \[--chain-id CHAIN\_ID]

Sets the ID of the chain. Default: `100`.

***

_**ibft-validators-prefix-path**_

SyntaxExample

genesis \[--ibft-validators-prefix-path IBFT\_VALIDATORS\_PREFIX\_PATH]

Prefix path for validator folder directory. Needs to be present if the flag `ibft-validator` is omitted.

***

_**ibft-validator**_

SyntaxExample

genesis \[--ibft-validator IBFT\_VALIDATOR\_LIST]

Sets passed in addresses as IBFT validators. Needs to be present if the flag `ibft-validators-prefix-path` is omitted.

***

_**block-gas-limit**_

SyntaxExample

genesis \[--block-gas-limit BLOCK\_GAS\_LIMIT]

Refers to the maximum amount of gas used by all operations in a block. Default: `5242880`.

***

_**consensus**_

SyntaxExample

genesis \[--consensus CONSENSUS\_PROTOCOL]

Sets consensus protocol. Default: `pow`.

***

_**bootnode**_

SyntaxExample

genesis \[--bootnode BOOTNODE\_URL]

Multiaddr URL for p2p discovery bootstrap. This flag can be used multiple times. Instead of an IP address, the DNS address of the bootnode can be provided.

***

_**max-validator-count**_

SyntaxExample

genesis \[--max-validator-count MAX\_VALIDATOR\_COUNT]

The maximum number of stakers able to join the validator set in a PoS consensus. This number cannot exceed the value of MAX\_SAFE\_INTEGER (2^53 - 2).

***

_**min-validator-count**_

SyntaxExample

genesis \[--min-validator-count MIN\_VALIDATOR\_COUNT]

The minimum number of stakers needed to join the validator set in a PoS consensus. This number cannot exceed the value of max-validator-count. Defaults to 1.

***

#### Operator Commands <a href="#operator-commands" id="operator-commands"></a>

**Peer Commands**

| **Command**  | **Description**                                                                     |
| ------------ | ----------------------------------------------------------------------------------- |
| peers add    | Adds a new peer using their libp2p address                                          |
| peers list   | Lists all the peers the client is connected to through libp2p                       |
| peers status | Returns the status of a specific peer from the peers list, using the libp2p address |

**peers add flags**

_**addr**_

SyntaxExample

peers add --addr PEER\_ADDRESS

Peer's libp2p address in the multiaddr format.

***

_**grpc-address**_

SyntaxExample

peers add \[--grpc-address GRPC\_ADDRESS]

Address of the gRPC API. Default: `127.0.0.1:9632`.

**peers list flags**

_**grpc-address**_

SyntaxExample

peers list \[--grpc-address GRPC\_ADDRESS]

Address of the gRPC API. Default: `127.0.0.1:9632`.

**peers status flags**

_**peer-id**_

SyntaxExample

peers status --peer-id PEER\_ID

Libp2p node ID of a specific peer within p2p network.

***

_**grpc-address**_

SyntaxExample

peers status \[--grpc-address GRPC\_ADDRESS]

Address of the gRPC API. Default: `127.0.0.1:9632`.

**IBFT Commands**

| **Command**     | **Description**                                                                                       |
| --------------- | ----------------------------------------------------------------------------------------------------- |
| ibft snapshot   | Returns the IBFT snapshot                                                                             |
| ibft candidates | Queries the current set of proposed candidates, as well as candidates that have not been included yet |
| ibft propose    | Proposes a new candidate to be added/removed from the validator set                                   |
| ibft status     | Returns the overall status of the IBFT client                                                         |
| ibft switch     | Add fork configurations into genesis.json file to switch IBFT type                                    |

**ibft snapshot flags**

_**number**_

SyntaxExample

ibft snapshot \[--number BLOCK\_NUMBER]

The block height (number) for the snapshot.

***

_**grpc-address**_

SyntaxExample

ibft snapshot \[--grpc-address GRPC\_ADDRESS]

Address of the gRPC API. Default: `127.0.0.1:9632`.

**ibft candidates flags**

_**grpc-address**_

SyntaxExample

ibft candidates \[--grpc-address GRPC\_ADDRESS]

Address of the gRPC API. Default: `127.0.0.1:9632`.

**ibft propose flags**

_**vote**_

SyntaxExample

ibft propose --vote VOTE

Proposes a change to the validator set. Possible values: `[auth, drop]`.

***

_**addr**_

SyntaxExample

ibft propose --addr ETH\_ADDRESS

Address of the account to be voted for.

***

_**grpc-address**_

SyntaxExample

peers add \[--grpc-address GRPC\_ADDRESS]

Address of the gRPC API. Default: `127.0.0.1:9632`.

**ibft status flags**

_**grpc-address**_

SyntaxExample

peers list \[--grpc-address GRPC\_ADDRESS]

Address of the gRPC API. Default: `127.0.0.1:9632`.

**ibft switch flags**

_**chain**_

SyntaxExample

ibft switch \[--chain GENESIS\_FILE]

Specifies the genesis file to update. Default: `test`.

***

_**type**_

SyntaxExample

ibft switch \[--type TYPE]

Specifies the IBFT type to switch. Possible values: `[PoS]`.

***

_**deployment**_

SyntaxExample

ibft switch \[--deployment DEPLOYMENT]

Specifies the height of contract deployment. Only available with PoS.

***

_**from**_

SyntaxExample

ibft switch \[--from FROM]

***

_**max-validator-count**_

SyntaxExample

ibft switch \[--max-validator-count MAX\_VALIDATOR\_COUNT]

The maximum number of stakers able to join the validator set in a PoS consensus. This number cannot exceed the value of MAX\_SAFE\_INTEGER (2^53 - 2).

***

_**min-validator-count**_

SyntaxExample

ibft switch \[--min-validator-count MIN\_VALIDATOR\_COUNT]

The minimum number of stakers needed to join the validator set in a PoS consensus. This number cannot exceed the value of max-validator-count. Defaults to 1.

Specifies the beginning height of the fork.

**Transaction Pool Commands**

| **Command**      | **Description**                                |
| ---------------- | ---------------------------------------------- |
| txpool status    | Returns the number of transactions in the pool |
| txpool subscribe | Subscribes for events in the transaction pool  |

**txpool status flags**

_**grpc-address**_

SyntaxExample

txpool status \[--grpc-address GRPC\_ADDRESS]

Address of the gRPC API. Default: `127.0.0.1:9632`.

**txpool subscribe flags**

_**grpc-address**_

SyntaxExample

txpool subscribe \[--grpc-address GRPC\_ADDRESS]

Address of the gRPC API. Default: `127.0.0.1:9632`.

***

_**promoted**_

SyntaxExample

txpool subscribe \[--promoted LISTEN\_PROMOTED]

Subscribes for promoted tx events in the TxPool.

***

_**dropped**_

SyntaxExample

txpool subscribe \[--dropped LISTEN\_DROPPED]

Subscribes for dropped tx events in the TxPool.

***

_**demoted**_

SyntaxExample

txpool subscribe \[--demoted LISTEN\_DEMOTED]

Subscribes for demoted tx events in the TxPool.

***

_**added**_

SyntaxExample

txpool subscribe \[--added LISTEN\_ADDED]

Subscribes for added tx events to the TxPool.

***

_**enqueued**_

SyntaxExample

txpool subscribe \[--enqueued LISTEN\_ENQUEUED]

Subscribes for enqueued tx events in the account queues.

***

**Blockchain commands**

| **Command** | **Description**                                                                   |
| ----------- | --------------------------------------------------------------------------------- |
| status      | Returns the status of the client. The detailed response can be found below        |
| monitor     | Subscribes to a blockchain event stream. The detailed response can be found below |
| version     | Returns the current version of the client                                         |

**status flags**

_**grpc-address**_

SyntaxExample

status \[--grpc-address GRPC\_ADDRESS]

Address of the gRPC API. Default: `127.0.0.1:9632`.

**monitor flags**

_**grpc-address**_

SyntaxExample

monitor \[--grpc-address GRPC\_ADDRESS]

Address of the gRPC API. Default: `127.0.0.1:9632`.

***

#### Secrets Commands <a href="#secrets-commands" id="secrets-commands"></a>

| **Command**      | **Description**                                                                           |
| ---------------- | ----------------------------------------------------------------------------------------- |
| secrets init     | Initializes the private keys to the corresponding secrets manager                         |
| secrets generate | Generates a secrets manager configuration file which can be parsed by the EVMBuilder Edge |

**secrets init flags**

_**config**_

SyntaxExample

secrets init \[--config SECRETS\_CONFIG]

Sets the path to the SecretsManager config file. Used for Hashicorp Vault. If omitted, the local FS secrets manager is used.

***

_**data-dir**_

SyntaxExample

secrets init \[--data-dir DATA\_DIRECTORY]

Sets the directory for the EVMBuilder Edge data if the local FS is used.

**secrets generate flags**

_**dir**_

SyntaxExample

secrets generate \[--dir DATA\_DIRECTORY]

Sets the directory for the secrets manager configuration file Default: `./secretsManagerConfig.json`

***

_**type**_

SyntaxExample

secrets generate \[--type TYPE]

Specifies the type of the secrets manager \[`hashicorp-vault`]. Default: `hashicorp-vault`

***

_**token**_

SyntaxExample

secrets generate \[--token TOKEN]

Specifies the access token for the service

***

_**server-url**_

SyntaxExample

secrets generate \[--server-url SERVER\_URL]

Specifies the server URL for the service

***

_**name**_

SyntaxExample

secrets generate \[--name NODE\_NAME]

Specifies the name of the node for on-service record keeping. Default: `z-edge-node`

***

_**namespace**_

SyntaxExample

secrets generate \[--namespace NAMESPACE]

Specifies the namespace used for the Hashicorp Vault secrets manager. Default: `admin`

***

#### Responses <a href="#responses" id="responses"></a>

**Status Response**

The response object is defined using Protocol Buffers.

minimal/proto/system.proto

Copy

```
message ServerStatus {
    int64 network = 1;

    string genesis = 2;

    Block current = 3;

    string p2pAddr = 4;

    message Block {
        int64 number = 1;
        string hash = 2;
    }
}
```

**Monitor Response**

minimal/proto/system.proto

Copy

```
message BlockchainEvent {
    // The "repeated" keyword indicates an array
    repeated Header added = 1;
    repeated Header removed = 2;

    message Header {
        int64 number = 1;
        string hash = 2;
    }
}
```

#### Utilities <a href="#utilities" id="utilities"></a>

**loadbot flags**

_**tps**_

SyntaxExample

loadbot \[--tps NUMBER\_OF\_TXNS\_PER\_SECOND]

The number of transactions per second to send. Default: `100`.

***

_**mode**_

SyntaxExample

loadbot \[--mode MODE]

Sets the loadbot run mode \[`transfer`, `deploy`]. Default: `transfer`.

***

_**chain-id**_

SyntaxExample

loadbot \[--chain-id CHAIN\_ID]

Sets the network chain ID for transactions. Default: `100`.

***

_**gas-price**_

SyntaxExample

loadbot \[--gas-price GAS\_PRICE]

The gas price that should be used for the transactions. If omitted, the average gas price is fetched from the network.

***

_**gas-limit**_

SyntaxExample

loadbot \[--gas-limit GAS\_LIMIT]

The gas limit that should be used for the transactions. If omitted, the gas limit is estimated before starting the loadbot.

***

_**grpc-address**_

SyntaxExample

loadbot --grpc-address GRPC\_ADDRESS

The GRPC endpoint used to send transactions

***

_**detailed**_

SyntaxExample

loadbot \[--detailed DETAILED]

Flag indicating if the error logs should be shown. Default: `false`.

***

_**contract**_

SyntaxExample

loadbot \[--contract CONTRACT\_PATH]

The path to the contract JSON artifact containing the bytecode. If omitted, a default contract is used.

***

_**sender**_

SyntaxExample

loadbot \[--sender ADDRESS]

Address of the sender account.

***

_**receiver**_

SyntaxExample

loadbot \[--receiver ADDRESS]

Address of the receiver account.

***

_**jsonrpc**_

SyntaxExample

loadbot \[--jsonrpc ENDPOINT]

A JSON RPC endpoint used to send transactions.

***

_**count**_

SyntaxExample

loadbot \[--count COUNT]

The total number of transactions to send. Default: `1000`.

***

_**value**_

SyntaxExample

loadbot \[--value VALUE]

The value to send in each transaction.

***

_**max-conns**_

SyntaxExample

loadbot \[--max-conns MAX\_CONNECTIONS\_COUNT]

Sets the maximum no.of connections allowed per host. Default: `2*tps`.

***

**backup flags**

_**grpc-address**_

SyntaxExample

backup \[--grpc-address GRPC\_ADDRESS]

Address of the gRPC API. Default: `127.0.0.1:9632`.

***

_**out**_

SyntaxExample

backup \[--out OUT]

Path of archive file to save.

***

_**from**_

SyntaxExample

from \[--from FROM]

The beginning height of blocks in archive. Default: 0.

***

_**to**_

SyntaxExample

to \[--to TO]

The end height of blocks in archive.

***

#### Genesis Template <a href="#genesis-template" id="genesis-template"></a>

The genesis file should be used to set the initial state of the blockchain (ex. if some accounts should have a starting balance).

The following _./genesis.json_ file is generated:

Copy

```
{
    "name": "example",
    "genesis": {
        "nonce": "0x0000000000000000",
        "gasLimit": "0x0000000000001388",
        "difficulty": "0x0000000000000001",
        "mixHash": "0x0000000000000000000000000000000000000000000000000000000000000000",
        "coinbase": "0x0000000000000000000000000000000000000000",
        "parentHash": "0x0000000000000000000000000000000000000000000000000000000000000000"
    },
    "params": {
        "forks": {},
        "chainID": 100,
        "engine": {
            "pow": {}
        }
    },
    "bootnodes": []
}
```

**Data Directory**

When executing the _data-dir_ flag, a **test-chain** folder is generated. The folder structure consists of the following sub-folders:

* **blockchain** - Stores the LevelDB for blockchain objects
* **trie** - Stores the LevelDB for the Merkle tries
* **keystore** - Stores private keys for the client. This includes the libp2p private key and the sealing/validator private key
* **consensus** - Stores any consensus information that the client might need while working

#### Resources <a href="#resources" id="resources"></a>

* [**Protocol Buffers**](https://developers.google.com/protocol-buffers)
