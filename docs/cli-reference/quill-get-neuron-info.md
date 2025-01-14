# quill get-neuron-info

Displays available information about a neuron.

## Basic usage

The basic syntax for running `quill get-neuron-info` commands is:

``` bash
quill get-neuron-info [option] <identifier>
```

## Arguments

| Argument       | Description            |
|----------------|------------------------|
| `<identifier>` | The neuron identifier. |

## Flags

| Flag           | Description                                        |
|----------------|----------------------------------------------------|
| `--dry-run`    | Will display the query, but not send it.           |
| `-h`, `--help` | Displays usage information.                        |
| `-y-`, `--yes` | Skips confirmation and sends the message directly. |

## Examples

The `quill get-neuron-info` command is used to get information about a neuron, such as its voting power and age.

For example, to look up the neuron 4966884161088437903:

```sh
quill get-neuron-info 4966884161088437903
```

This would produce a response like:

```candid
(
  variant {
    Ok = record {
      dissolve_delay_seconds = 26_738_334 : nat64;
      recent_ballots = vec {
        record {
            vote = 1 : int32;
            proposal_id = opt record { id = 107_965 : nat64; };
        };
      };
      created_timestamp_seconds = 1_652_950_497 : nat64;
      state = 2 : int32;
      stake_e8s = 300_000_000_010_000 : nat64;
      joined_community_fund_timestamp_seconds = null;
      retrieved_at_timestamp_seconds = 1_676_591_316 : nat64;
      known_neuron_data = null;
      voting_power = 331_773_250_353_290 : nat64;
      age_seconds = 0 : nat64;
    }
  },
)
```

"e8s" is a shorthand for meaning the number of 1e-8s, or one-hundred-millionths, of an ICP in integer form; this response must be divided by 100,000,000 to get the real balance, which in this case would be 3000000.0001 ICP.

## Remarks

As this is a query call, it cannot be executed on an air-gapped machine, but does not require access to your keys.

For more information about neurons, see [Neurons].

[Neurons]: https://internetcomputer.org/docs/current/tokenomics/nns/nns-intro#neurons
