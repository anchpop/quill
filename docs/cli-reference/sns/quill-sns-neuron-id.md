# quill sns neuron-id 

Prints the SNS NeuronId. 

## Basic usage

The basic syntax for running `quill sns neuron-id` commands is:

``` bash
quill sns neuron-id [option]
```

## Flags

| Flag            | Description                                                    |
|-----------------|----------------------------------------------------------------|
| `-h`, `--help`  | Displays usage information.                                    |

## Options

| Option                          | Description                                               |
|---------------------------------|-----------------------------------------------------------|
| `--principal-id <PRINCIPAL_ID>` | Principal for which to get the SNS NeuronId.              |
| `--memo <MEMO>`                 | Memo used along with a Principal to get the SNS NeuronId. |

## Examples

The `quill sns neuron-id` command is used to display your SNS NeuronId, or the SNS NeuronId of a given principal.

For example, to view the default SNS NeuronId for the anonymous principal:

```sh
quill sns neuron-id --principal-id 2vxsx-fae --memo 0
```

This will produce the output:

```
SNS Neuron Id: bf03d242b370d2126fcd94f229f6525891f28d07833d36005bfac6c224ffa651
```
