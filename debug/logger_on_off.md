# --logger_on_off name=<ctx_name> enable=<on|off>

## Description
Disables or enables a specific logger component on the VeloCloud Edge. Loggers are identified by their context name (`<ctx_name>`). This command allows administrators to control the verbosity of different logging components (e.g., VCRP, VCMP, FLOW_STATS) by turning their respective logs `on` or `off`. This is particularly useful for troubleshooting specific issues by focusing log collection on relevant modules.

## Arguments
| Argument    | Description                                                                 | Values / Example                     |
|-------------|-----------------------------------------------------------------------------|--------------------------------------|
| `name=<ctx_name>` | Specifies the context name of the logger to be configured. This is a string that uniquely identifies the logging component. | e.g., `VCMP_DEBUG`, `FLOW_STATS`, `KERNEL_EVENTS` |
| `enable=<on|off>` | Sets the desired state for the specified logger. `on` enables logging for the context, while `off` disables it. | `on`, `off`                          |

## Example Usage
To enable logging for the `VCMP_DEBUG` context:
```shell
example_com:velocli> debug --logger_on_off name=VCMP_DEBUG enable=on
```

To disable logging for the `FLOW_STATS` context:
```shell
example_com:velocli> debug --logger_on_off name=FLOW_STATS enable=off
```
If the command `debug --logger_on_off` is issued without parameters, it may list available logger contexts or display current logger states, though the primary described function involves specifying `name` and `enable` to modify a logger's state.