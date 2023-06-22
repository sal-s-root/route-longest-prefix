# route-longest-prefix

Select the most specific matching route for an IP destination.

## Run

Python 3.8 or later; no third-party packages or cloud credentials are required.

```sh
python3 tool.py examples/input.json
cat examples/input.json | python3 tool.py -
python3 -m unittest -v
```

## Example

Input:

```json
{
  "destination": "10.0.1.5",
  "routes": [
    {
      "cidr": "0.0.0.0/0",
      "via": "gateway"
    },
    {
      "cidr": "10.0.1.0/24",
      "via": "local"
    }
  ]
}
```

Result:

```json
{
  "route": {
    "cidr": "10.0.1.0/24",
    "via": "local"
  }
}
```

The command writes JSON to standard output. Exit 0 means evaluation completed;
a finding in the output may still require attention. Invalid input returns exit 2,
with an error on standard error and no result on standard output.

## Operational scope

Does not model metrics, policy routing, equal-cost multipath, or interface state.

The tool evaluates supplied data locally. It does not change hosts, deploy
resources, or establish production compliance. Example identifiers and observations
are test fixtures. Keep credentials and private inventory out of Git.

## Design and verification

See [NOTES.md](NOTES.md) for the input contract, verification, and integration notes.
Related utilities: [port-range-merger](https://github.com/sal-s-root/port-range-merger), [latency-percentile-calculator](https://github.com/sal-s-root/latency-percentile-calculator).
