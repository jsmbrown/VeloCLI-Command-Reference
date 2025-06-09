# --atp_profile

## Description
Enable/Disable ATP Profiling. This command is used to toggle the ATP (Application Traffic Profiling) feature on the VeloCloud Edge. When this feature is enabled, the Edge collects specific data related to network traffic or application behavior. This data can then be used for analysis, aiding in performance monitoring, diagnostics, or security assessments.

## Arguments
This command does not take any arguments.

## Example usage
```
example_com:velocli> debug --atp_profile
usage: debug.py [-h] [--mode_link] [--timeout TIMEOUT SECONDS]
                [--logfile LOGFILE] [--limit N] [-v]
                [--biz_pol_dump [[all | segment-id] [[all | policy-name]
                ...]]] [--netflow_intervals] [--netflow_collectors]
                [--netflow_filters [<collector_id>]] [--bw_testing_dump]
                [--chat_stats [[sip=] [dip=] [dport=] [app_id=]
```
**Note:** The `debug --atp_profile` command is designed to enable or disable the ATP Profiling feature. The output shown in the example above is a general usage message for the `debug.py` script. Typically, a command that toggles a feature might provide a confirmation message indicating the new state of the feature (e.g., "ATP Profiling enabled" or "ATP Profiling disabled"), though this is not shown in the provided example output.

## Field descriptions
This command is a toggle command and does not produce tabular output with specific fields. Its primary function is to change the operational state of the ATP Profiling feature on the VeloCloud Edge.