# -v, --verbose

## Description
The `-v` or `--verbose` option modifies the output of `debug` commands to be in raw JSON format instead of the default human-readable, formatted display. This is particularly useful when the output needs to be consumed or parsed by scripts or other automated tools.

## Arguments
This option does not take any arguments.

## Example usage
The following command enables verbose mode for the `debug` utility:
```
example_com:velocli> debug -v
```
Alternatively, the long form can be used:
```
example_com:velocli> debug --verbose
```
When this option is active, any subsequent `debug` command (e.g., `debug --routes`, `debug --chat_stats`) will produce output in raw JSON format instead of its standard formatted display. For instance, if `debug --routes` is executed after `-v` (or `--verbose`) has been specified, the route table information will be presented as a JSON object.

## Field descriptions
When the `-v` or `--verbose` option is active, the output of `debug` commands is presented in raw JSON format. The "fields" in this context are the keys within the JSON object. The specific keys and their corresponding values will vary depending on the particular `debug` command being executed. For details on the JSON structure and keys for a specific command, refer to the documentation of that command, noting that its output will be JSON when verbose mode is active.