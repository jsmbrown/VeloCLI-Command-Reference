# --webroot_set_loglevel &lt;loglevel&gt; &lt;logging_type&gt;

## Description
Sets the logging level and output destination for Webroot component logs on the VeloCloud Edge. This command helps in troubleshooting issues related to the Webroot integration by controlling the verbosity and location of its logs.

## Arguments (mandatory)
| Argument         | Description                                                                                                                                                                                                                            |
|------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `<loglevel>`     | Specifies the verbosity of the Webroot logs. Valid integer values are:<ul><li>`1`: Error - Log only error messages.</li><li>`2`: Warning - Log error and warning messages.</li><li>`3`: Info - Log error, warning, and informational messages.</li><li>`4`: Debug - Log error, warning, informational, and debug messages.</li><li>`5`: Trace - Log all messages, including detailed trace information (most verbose).</li></ul> |
| `<logging_type>` | Specifies where the Webroot logs will be written. Valid values are:<ul><li>`edge_only`: Logs are written to the standard Edge log file (`edged.log`) or can be viewed via `debug.py --dbgctl`.</li><li>`bcti_only`: All Webroot logs are exclusively written to `bcti.log`. **Note:** This option can impact system performance.</li><li>`both`: Webroot logs are written to both the standard Edge log (`edged.log`/`dbgctl`) and `bcti.log`. **Note:** This option can impact system performance.</li></ul> |

## Example Usage
To set the Webroot log level to 'Info' (3) and direct logs only to the standard Edge logging mechanisms:
```
example_com:velocli> debug --webroot_set_loglevel 3 edge_only
```

To set the Webroot log level to 'Debug' (4) and direct logs to both standard Edge logs and `bcti.log`:
```
example_com:velocli> debug --webroot_set_loglevel 4 both
```

If arguments are not provided, the command will return an error:
```
example_com:velocli> debug --webroot_set_loglevel
Insufficient Arguments

example_com:velocli>
```

## Field Descriptions
This command is used to configure logging behavior and does not produce tabular output. Upon successful execution, it modifies the Webroot logging settings on the Edge.