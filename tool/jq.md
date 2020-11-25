# jq

jq - Command-line JSON processor

## Map

Retrieve all the keys of a map using function
[`keys`](https://stedolan.github.io/jq/manual/#keys,keys_unsorted):

```sh
# JSON:
#
# {
#   "k1" : "v1",
#   "k2" : "v2"
# }
#
echo $json | jq "keys"
#
# [
#   "k1",
#   "k2"
# ]
#
```

## Raw Output

With this option `--raw-output`/`-r`, if the filter's result is a string then it will be written
directly to standard output rather than being formatted as a JSON string with
quotes. This can be useful for making jq filters talk to non-JSON-based systems.

Find the first element (0) of the array and return the string value without
quote:

```sh
# JSON:
#
# [
#   "apple",
#   "banana",
#   "coconut"
# ]
#
echo $json | jq -r ".[0]"
#
# apple
#
```

## References

- jq Manual (development version) <https://stedolan.github.io/jq/manual/>
