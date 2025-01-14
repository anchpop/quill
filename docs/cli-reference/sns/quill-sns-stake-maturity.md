# quill sns stake-maturity

Signs a ManageNeuron message to stake a percentage of a neuron's maturity.

A neuron's total stake is the combination of its staked governance tokens and staked maturity.

## Basic usage

The basic syntax for running `quill sns stake-maturity` commands is:

```bash
quill sns stake-maturity <NEURON_ID> --percentage <PERCENTAGE> [option]
```

## Arguments

| Argument      | Description                        |
|---------------|------------------------------------|
| `<NEURON_ID>` | The ID of the neuron to configure. |

## Flags

| Flag           | Description                 |
|----------------|-----------------------------|
| `-h`, `--help` | Displays usage information. |

## Options

| Option                      | Description                                             |
|-----------------------------|---------------------------------------------------------|
| `--percentage <PERCENTAGE>` | The percentage of the current maturity to stake (1-100) |
