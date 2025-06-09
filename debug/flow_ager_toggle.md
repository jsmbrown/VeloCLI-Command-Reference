# --flow_ager_toggle [enable_or_disable] [timer_iterval_secs] [idle_timeout_secs]

## Description
Enables or disables the flow ager and configures its associated timers. The flow ager is responsible for managing the lifecycle of network flows, including timing out idle flows.

## Arguments
| Argument             | Description                                                                 |
|----------------------|-----------------------------------------------------------------------------|
| `enable_or_disable`  | Set to `1` to enable the flow ager, or `0` to disable it.                   |
| `timer_iterval_secs` | Specifies the timer interval for the flow ager in seconds. This determines how frequently the flow ager checks for idle flows. |
| `idle_timeout_secs`  | Specifies the idle timeout for flows in seconds. If a flow is idle for this duration, it will be removed by the flow ager. |

## Example usage
To enable the flow ager with a timer interval of 60 seconds and an idle timeout of 300 seconds:
```
example_com:velocli> debug --flow_ager_toggle 1 60 300
```
To disable the flow ager (timer values might be ignored or can be set to defaults like 0):
```
example_com:velocli> debug --flow_ager_toggle 0 0 0
```

## Field descriptions
| Column | Description |
|---|---|
| N/A    | This command is used to configure the flow ager settings. It does not produce tabular output. Successful execution typically results in a confirmation message or no output if the change is applied silently. |