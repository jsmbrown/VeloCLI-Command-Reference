# --shr [enable|disable] [stats_interval_ms]

## Description
This command is used to configure the operational state (enabled or disabled) of a feature, potentially related to routing or Self-Healing Routes (SHR), and to set the interval for collecting its associated route statistics. The command's behavior is determined by the arguments provided:
- The first argument (`enable` or `disable`) dictates the feature's state. Internally, this often corresponds to `1` for enabled and `0` for disabled.
- The second argument (`stats_interval_ms`), if provided, specifies the interval in milliseconds at which route statistics should be collected.

## Arguments (optional)
The command expects arguments in a specific order. The `stats_interval_ms` argument is optional.

| Argument            | Description                                                                                             |
|---------------------|---------------------------------------------------------------------------------------------------------|
| `enable`            | As the first positional argument, this keyword enables the feature (corresponding to an internal state of `1`). |
| `disable`           | As the first positional argument, this keyword disables the feature (corresponding to an internal state of `0`). |
| `stats_interval_ms` | An integer value provided as the second positional argument. This specifies the route statistics collection interval in milliseconds. This argument is optional. |

## Example usage
The following example shows the help message displayed when `debug --shr` is run without the required arguments, indicating that at least the first argument (`enable` or `disable`) is mandatory.
```
example_com:velocli> debug --shr
usage: debug.py [-h] [--mode_link] [--timeout TIMEOUT SECONDS]
                [--logfile LOGFILE] [--limit N] [-v]
                [--biz_pol_dump [[all | segment-id] [[all | policy-name]
                ...]]] [--netflow_intervals] [--netflow_collectors]
                [--netflow_filters [<collector_id>]] [--bw_testing_dump]
                [--chat_stats [[sip=] [dip=] [dport=] [app_id=]
```
A valid command invocation would look like:
`example_com:velocli> debug --shr enable 5000`
This would enable the feature and set the statistics interval to 5000 milliseconds.

## Field descriptions
| Column | Description |
|---|---|
| N/A    | This command does not produce tabular output. The example provided shows the command's usage help, which is typically displayed when required arguments are missing or arguments are provided incorrectly. |