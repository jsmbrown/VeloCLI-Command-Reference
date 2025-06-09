# -t, --time

## Description
Appends a timestamp to the output of `debug` commands. This flag is intended to be used in conjunction with other `debug` subcommands to help in correlating events or analyzing logs over time.

## Arguments
This command does not take any arguments.

## Example Usage
The `--time` (or `-t`) flag is designed to modify the output of other `debug` subcommands by adding a timestamp.

The example below shows an attempt to use the flag as `debug -t, --time`. This specific invocation syntax, or the absence of a required subcommand for the `debug` utility, leads to an error.
```
example_com:velocli> debug -t, --time
usage: debug.py [--timeout TIMEOUT SECONDS] [--logfile LOGFILE]
debug.py: error: argument --timeout: expected 1 argument
```
**Note on the error:** The error message `debug.py: error: argument --timeout: expected 1 argument` suggests that the command line parser may have misinterpreted the input (potentially confusing `--time` with `--timeout`) or that the `debug` script requires other mandatory arguments or subcommands that were not supplied. The syntax `debug -t, --time` where both short and long form flags are listed together with a comma is unusual for command-line utilities. Typically, a user would specify either `-t` or `--time`.

**Intended Usage:**
To correctly use this functionality, pair the `-t` or `--time` flag with a specific `debug` subcommand. For instance:

Using the short form:
`example_com:velocli> debug -t --routes`

Or using the long form:
`example_com:velocli> debug --time --routes`

Executing such a command would display the output of the specified subcommand (e.g., `--routes`), with timestamps included. The exact format of the timestamp and its placement (e.g., prepended to each line, or a single timestamp for the entire output block) depends on the specific implementation within the `debug` utility.