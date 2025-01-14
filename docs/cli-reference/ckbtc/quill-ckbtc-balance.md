# quill ckbtc balance

Sends a message to check the provided user's ckBTC balance.

## Basic usage

The basic syntax for running `quill ckbtc balance` commands is:

```bash
quill ckbtc balance [option]
```

## Flags

| Flag           | Description                                        |
|----------------|----------------------------------------------------|
| `--dry-run`    | Will display the query, but not send it.           |
| `-h`, `--help` | Displays usage information.                        |
| `--testnet`    | Uses ckTESTBTC instead of ckBTC.                   |
| `-y`, `--yes`  | Skips confirmation and sends the message directly. |

## Options

| Argument                          | Description                                      |
|-----------------------------------|--------------------------------------------------|
| `--of <OF>`                       | The account to check. Optional if a key is used. |
| `--of-subaccount <OF_SUBACCOUNT>` | The subaccount of the account to check.          |

## Examples

The `quill ckbtc balance` command is used to check an account's ckBTC balance. For example, to see how much ckBTC is held by the principal `fdsgv-62ihb-nbiqv-xgic5-iefsv-3cscz-tmbzv-63qd5-vh43v-dqfrt-pae`:

```sh
quill ckbtc balance --of fdsgv-62ihb-nbiqv-xgic5-iefsv-3cscz-tmbzv-63qd5-vh43v-dqfrt-pae
```

You can check your own balance by leaving off the `--of` parameter:

```sh
quill ckbtc balance --pem-file ./id.pem
```

Subaccounts can be provided explicitly:

```sh
quill ckbtc balance --of fdsgv-62ihb-nbiqv-xgic5-iefsv-3cscz-tmbzv-63qd5-vh43v-dqfrt-pae --of-subaccount 01
```

Or as part of an ICRC-1 account ID:

```sh
quill ckbtc balance --of fdsgv-62ihb-nbiqv-xgic5-iefsv-3cscz-tmbzv-63qd5-vh43v-dqfrt-pae-gegmhna.3
```

This will return a response like:

```candid
(4_000_000 : nat)
```

The response contains the number of *satoshis*, i.e. hundred-millionths of a ckBTC token. This response would mean the user has 0.04 ckBTC.

## Remarks

The `--of` parameter is required if a signing key is not provided.

As this is a query call, it cannot be executed on an air-gapped machine, but does not require access to your keys.
