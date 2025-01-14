# quill public-ids

Prints the principal id and the account id.

## Basic usage

The basic syntax for running `quill public-ids` commands is:

``` bash
quill public-ids [option]
```

## Flags

| Flag                  | Description                                                     |
|-----------------------|-----------------------------------------------------------------|
| `-h`, `--help`        | Displays usage information.                                     |
| `--genesis-dfn`       | Additionally prints the legacy DFN address for Genesis claims.  |
| `--display-on-ledger` | Additionally prints the principal on an attached Ledger device. |

## Options

| Option                          | Description                                |
|---------------------------------|--------------------------------------------|
| `--principal-id <PRINCIPAL_ID>` | Principal for which to get the account id. |
| `--subaccount <SUBACCOUNT>`     | Subaccount to include in the account ID.   |

## Examples

The `quill public-ids` command is used to display your principal and account ID, or the ID of a given principal.

For example, to view the default account ID for the anonymous principal:

```sh
quill public-ids --principal-id 2vxsx-fae
```

This will produce the output:

```
Principal id: 2vxsx-fae
Legacy account id: 1c7a48ba6a562aa9eaa2481a9049cdf0433b9738c992d698c31d8abf89cadc79
```

It can also be used to display ICRC-1 account IDs:

```sh
quill public-ids --subaccount 010203
```

This will produce output like:

```
Principal id: fdsgv-62ihb-nbiqv-xgic5-iefsv-3cscz-tmbzv-63qd5-vh43v-dqfrt-pae
Legacy account id: 0ae94165785f2ffb9c56ebc84f3d13299f28db78c80b1db43c0d114eed6105af
ICRC-1 account id: fdsgv-62ihb-nbiqv-xgic5-iefsv-3cscz-tmbzv-63qd5-vh43v-dqfrt-pae-al4mwai.10203
```
