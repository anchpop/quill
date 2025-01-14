# quill sns configure-dissolve-delay

Signs a ManageNeuron message to configure the dissolve delay of a neuron. With this command neuron
holders can start dissolving, stop dissolving, or increase dissolve delay. The dissolve delay of a
neuron determines its voting power, its ability to vote, its ability to make proposals, and other
actions it can take (such as disbursing).

## Basic usage

The basic syntax for running `quill sns configure-dissolve-delay` commands is:

```bash
quill sns configure-dissolve-delay <NEURON_ID> [option]
```

## Arguments

| Argument      | Description                        |
|---------------|------------------------------------|
| `<NEURON_ID>` | The ID of the neuron to configure. |

## Flags

| Flag                 | Description                                   |
|----------------------|-----------------------------------------------|
| `-h`, `--help`       | Displays usage information.                   |
| `--start-dissolving` | The neuron will go into the dissolving state. |
| `--stop-dissolving`  | The neuron will exit the dissolving state.    |

## Options

| Option                                                | Description                                                              |
|-------------------------------------------------------|--------------------------------------------------------------------------|
| `-a`, `--additional-dissolve-delay-seconds <SECONDS>` | Additional number of seconds to add to the dissolve delay of the neuron. |

## Remarks

When the neuron starts dissolving, a countdown timer will begin. When the timer is exhausted (i.e. dissolve_delay_seconds amount of time has elapsed), the neuron can be disbursed. When the neuron stops dissolving, whatever amount of dissolve delay seconds is left in the countdown timer is stored. A neuron's dissolve delay can be extended (for instance to increase voting power) by using the `--additional_dissolve_delay_seconds` flag. If the neuron is already dissolving and this argument is specified, the neuron will stop dissolving and begin aging.
