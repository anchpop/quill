# quill ckbtc update-balance

Signs a message to mint ckBTC from previously deposited BTC

## Basic usage

The basic syntax for running `quill ckbtc update-balance` commands is:

```bash
quill ckbtc update-balance [option]
```

## Flags

| Flag           | Description                      |
|----------------|----------------------------------|
| `-h`, `--help` | Displays usage information.      |
| `--testnet`    | Uses ckTESTBTC instead of ckBTC. |

## Options

| Argument                    | Description                     |
|-----------------------------|---------------------------------|
| `--sender <SENDER>`         | The account to mint ckBTC to    |
| `--subaccount <SUBACCOUNT>` | The subaccount to mint ckBTC to |

## Examples

The `quill ckbtc update-balance` command is used to convert already-deposited BTC into ckBTC:

```sh
# After transferring BTC:
quill ckbtc update-balance
```

This will return a response like:

```candid
(
    variant {
        Ok = vec {
            variant {
                Minted = record {
                    block_index = 5_581_035 : nat64;
                    minted_amount = 4_000_000 : nat64;
                    utxo = record { ... };
                }
            }
        }
    }
)
```

The provided block index can be looked up on the [IC dashboard].

The returned amount is the number of *satoshis*, or hundred-millionths of a ckBTC; in this case the user would have minted 0.04 ckBTC.

## Remarks

The `--sender` flag is required if a signing key is not provided.

As this is an update call, it will not actually make the request, but rather generate a signed and packaged request that can be sent from anywhere. You can use the `--qr` flag to display it as a QR code, or if you are not working with an air-gapped machine, you can pipe it to `quill send`.

[IC dashboard]: https://dashboard.internetcomputer.org/bitcoin/transactions
