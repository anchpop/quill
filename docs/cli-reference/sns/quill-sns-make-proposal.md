# quill sns make-proposal

Signs a ManageNeuron message to submit a proposal. With this command, neuron holders can submit
proposals (such as a Motion Proposal) to be voted on by other neuron holders.

## Basic usage

The basic syntax for running `quill sns make-proposal` commands is:

```bash
quill sns make-proposal <PROPOSER_NEURON_ID> --proposal <PROPOSAL> [option]
```

## Flags

| Flag           | Description                 |
|----------------|-----------------------------|
| `-h`, `--help` | Displays usage information. |

## Options

| Option                  | Description                   |
|-------------------------|-------------------------------|
| `--proposal <PROPOSAL>` | The proposal to be submitted. |

## Remarks

Proposals must be formatted as candid records. For example:

```candid
(
    record {
        title = "SNS Launch";
        url = "https://dfinity.org";
        summary = "A motion to start the SNS";
        action = opt variant {
            Motion = record {
                motion_text = "I hereby raise the motion that the use of the SNS shall commence";
            }
        };
    }
)
```
