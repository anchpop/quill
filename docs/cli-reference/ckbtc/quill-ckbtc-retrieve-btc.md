# quill ckbtc retrieve-btc

Signs messages to retrieve BTC in exchange for ckBTC.

## Basic usage

The basic syntax for running `quill ckbtc retrieve-btc` commands is:

```bash
quill ckbtc retrieve-btc [option] <TO>
```

## Arguments

| Argument | Description                                                                             |
|----------|-----------------------------------------------------------------------------------------|
| `<TO>`   | The Bitcoin address to send the BTC to. Note that Quill does not validate this address. |

## Flags

| Flag                    | Description                                                            |
|-------------------------|------------------------------------------------------------------------|
| `--already-transferred` | Skips signing the transfer of ckBTC, signing only the request for BTC. |
| `-h`, `--help`          | Displays usage information.                                            |
| `--testnet`             | Uses ckTESTBTC instead of ckBTC.                                       |

## Options

| Option                                | Description                                    |
|---------------------------------------|------------------------------------------------|
| `--amount <AMOUNT>`                   | The quantity, in decimal BTC, to convert.      |
| `--fee <FEE>`                         | The expected fee for the ckBTC transfer.       |
| `--from-subaccount <FROM_SUBACCOUNT>` | The subaccount to transfer the ckBTC from.     |
| `--memo <MEMO>`                       | An integer memo for the ckBTC transfer.        |
| `--satoshis <SATOSHIS>`               | The quantity, in integer satoshis, to convert. |

## Examples

The `quill ckbtc retrieve-btc` command is used to convert ckBTC to BTC.

For example, to convert 0.5 ckBTC to BTC at the Bitcoin address `3L2Uyh1eHpfPyPayqrh5WjfnTzWiG4xPLu`:

```sh
quill ckbtc retrieve-btc 3L2Uyh1eHpfPyPayqrh5WjfnTzWiG4xPLu --amount 0.5
```

This command generates two messages by default; a transfer of ckBTC to the minting canister, and a request for BTC. However, if you have already made this transfer, you can use the `--already-transferred` flag to skip the first message:

```sh
quill ckbtc retrieve-btc 3L2Uyh1eHpfPyPayqrh5WjfnTzWiG4xPLu --amount 0.5 --already-transferred
```

Bitcoin transactions take a while, so the response to the second message will not be a success state, but rather a block index:

```candid
(variant Ok = record { block_index = 52_151 : nat64; })
```

To check the status of this transfer:

```sh
quill ckbtc retrieve-btc-status 52151
```

This will produce a response like:

```candid
(
    variant {
        Confirmed = record {
            txid = blob "X\9f\11\85\0f0\a6c\84&R\1d5\de\b96Q}0\033\e9\a4\ce\8a\df@]\de\1d\ce\17";
        }
    }
)
```

## Remarks

The `quill ckbtc withdrawal-address` command can be used to get the address that retrievals are made via. 

As this is an update call, it will not actually make the request, but rather generate a signed and packaged request that can be sent from anywhere. You can use the `--qr` flag to display it as a QR code, or if you are not working with an air-gapped machine, you can pipe it to `quill send`.
