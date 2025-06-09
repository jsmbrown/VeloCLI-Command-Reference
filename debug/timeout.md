#	--timeout TIMEOUT (SECONDS)

##	Description
Overrides the default timeout of 2 seconds for `debug` commands. This allows subsequent `debug` commands in the same `velocli` session to wait longer for a response from the VeloCloud Edge. This is particularly useful for commands that might take more than the default 2 seconds to gather and return data.

##  Arguments
| Argument          | Description                                  |
|-------------------|----------------------------------------------|
| TIMEOUT (SECONDS) | **Required.** The new timeout value in seconds. |

##  Example usage
To set the timeout to 10 seconds for subsequent debug commands:
```
example_com:velocli> debug --timeout 10
```

If the `TIMEOUT (SECONDS)` argument is not provided, the command will return an error:
```
example_com:velocli> debug --timeout
usage: debug.py [--timeout TIMEOUT SECONDS] [--logfile LOGFILE]
debug.py: error: argument --timeout: expected 1 argument
```