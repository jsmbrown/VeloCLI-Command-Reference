#	--debug_bw_test

##	Description
Run a bandwidth test on the path(s) connected through an interface.

##  Arguments
This command does not take any arguments.

##  Example usage
```
example_com:velocli> debug --debug_bw_test
usage: debug.py [-h] [--mode_link] [--timeout TIMEOUT SECONDS]
                [--logfile LOGFILE] [--limit N] [-v]
                [--biz_pol_dump [[all | segment-id] [[all | policy-name]
                ...]]] [--netflow_intervals] [--netflow_collectors]
                [--netflow_filters [<collector_id>]] [--bw_testing_dump]
                [--chat_stats [[sip=] [dip=] [dport=] [app_id=]
```

##  Field Descriptions
The output of the `debug --debug_bw_test` command is the help message for an underlying script, `debug.py`. This script is utilized to perform various debugging tasks, including initiating bandwidth tests. The "fields" listed below correspond to the options available for the `debug.py` script as presented in its help message:

| Option/Argument                                               | Description                                                                                                |
|---------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|
| `-h`, `--help`                                                | Show this help message and exit.                                                                           |
| `--mode_link`                                                 | (Details not fully provided in the example output) Likely enables a specific mode for link-based testing.  |
| `--timeout TIMEOUT SECONDS`                                   | Specifies a timeout value in seconds for the script's operation.                                           |
| `--logfile LOGFILE`                                           | Designates a file to which the script's logging output will be written.                                    |
| `--limit N`                                                   | Restricts the operation, potentially by limiting the number of iterations or items processed.              |
| `-v`                                                          | Enables verbose output mode, providing more detailed information during execution.                         |
| `--biz_pol_dump [[all | segment-id] [[all | policy-name] ...]]` | Dumps business policy information. This can be optionally filtered by `segment-id` and `policy-name`.      |
| `--netflow_intervals`                                         | Displays information related to NetFlow intervals.                                                         |
| `--netflow_collectors`                                        | Displays information related to NetFlow collectors.                                                        |
| `--netflow_filters [<collector_id>]`                          | Displays NetFlow filters. The output can be optionally filtered by a specific `collector_id`.              |
| `--bw_testing_dump`                                           | Dumps data or status related to bandwidth testing procedures.                                              |
| `--chat_stats [[sip=] [dip=] [dport=] [app_id=]`              | Displays statistics for chat applications. The statistics can be filtered by source IP (`sip`), destination IP (`dip`), destination port (`dport`), and application ID (`app_id`). |