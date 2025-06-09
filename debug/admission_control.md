# --admission_control [<nothing> | enable [threshold <N>] | disable]

## Description
Manages and displays the status of admission control on the VeloCloud Edge. Admission control is a system protection mechanism that monitors memory buffer (mbuf) utilization. If mbuf usage exceeds a configured threshold while admission control is enabled, the system may take protective actions, such as dropping packets, to prevent instability due to resource exhaustion.

## Arguments (optional)
The command behavior depends on the argument provided:

| Argument                 | Description                                                                                                                               |
| ------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------- |
| (no argument)            | Displays the current admission control status, including maximum handoff buffers, current operational status (Enabled/Disabled), and the configured mbuf threshold percentage. This is the default action if no other arguments are provided. |
| `enable`                 | Enables admission control. If `threshold <N>` is not specified, it uses the previously configured threshold or a system default.        |
| `enable threshold <N>`   | Enables admission control and sets the mbuf (memory buffer) threshold percentage to `<N>`. `<N>` must be an integer (e.g., 30 for 30%). |
| `disable`                | Disables admission control.                                                                                                               |

## Example Usage
To display the current admission control status:
```
example_com:velocli> debug --admission_control
{
  "Max Handoff Buffers": 88470,
  "Status": "Enabled",
  "Threshold Percentage": 30
}
```
To enable admission control with a threshold of 25%:
```
example_com:velocli> debug --admission_control enable threshold 25
{
  "Max Handoff Buffers": 88470,
  "Status": "Enabled",
  "Threshold Percentage": 25
}
```
To disable admission control:
```
example_com:velocli> debug --admission_control disable
{
  "Max Handoff Buffers": 88470,
  "Status": "Disabled",
  "Threshold Percentage": 25
}
```

## Field Descriptions
When displaying the status, the following fields are shown:

| Field                  | Description                                                                                                                                                              |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `Max Handoff Buffers`  | The maximum number of handoff buffers available on the VeloCloud Edge. These buffers are utilized during packet processing.                                              |
| `Status`               | Indicates the current operational state of admission control. Possible values are "Enabled" or "Disabled".                                                                 |
| `Threshold Percentage` | The configured mbuf (memory buffer) utilization threshold, expressed as a percentage. If admission control is 'Enabled' and actual mbuf usage exceeds this percentage, the system may initiate measures like packet dropping to maintain stability. |