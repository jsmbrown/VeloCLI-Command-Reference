#	--l7_health_check_tbl_del &lt;seg-id&gt; &lt;dest-ip&gt; &lt;dst-port&gt;

##	Description
Deletes a specific entry from the Layer 7 (L7) health check hash table on the VeloCloud Edge. This table is used by the Edge to monitor the health of application servers or services, often as part of business policy enforcement or application-aware routing. Removing an entry stops the Edge from performing health checks for that specific destination (IP address and port combination) within the specified segment.

This command is typically used for troubleshooting or to manually intervene in the L7 health monitoring process.

##  Arguments
| Argument    | Description                                                                                                |
|-------------|------------------------------------------------------------------------------------------------------------|
| `&lt;seg-id&gt;`    | **Mandatory.** The segment ID associated with the L7 health check entry to be deleted.                     |
| `&lt;dest-ip&gt;`   | **Mandatory.** The destination IP address of the L7 health check target to be deleted.                     |
| `&lt;dst-port&gt;`  | **Mandatory.** The destination port number of the L7 health check target to be deleted (e.g., 80, 443). |

##  Example usage

**Attempting to run the command without mandatory arguments:**
If the command is invoked without the required arguments, the system will display the help text and usage instructions.
```
example_com:velocli> debug --l7_health_check_tbl_del
usage: debug.py [-h] [--mode_link] [--timeout TIMEOUT SECONDS]
                [--logfile LOGFILE] [--limit N] [-v]
                [--biz_pol_dump [[all | segment-id] [[all | policy-name]
                ...]]] [--netflow_intervals] [--netflow_collectors]
                [--netflow_filters [<collector_id>]] [--bw_testing_dump]
                [--chat_stats [[sip=] [dip=] [dport=] [app_id=]
... (help text continues, indicating missing arguments for --l7_health_check_tbl_del if it were fully listed) ...
```
*(The example output above is illustrative of a generic help message when arguments are missing. The actual help text might vary slightly or specifically point out the missing arguments for `--l7_health_check_tbl_del`.)*

**Successfully deleting an L7 health check entry:**
To delete an L7 health check entry for a service at IP `10.20.30.40` on port `8080` within segment `1`:
```
example_com:velocli> debug --l7_health_check_tbl_del 1 10.20.30.40 8080
L7 health check entry for segment 1, destination 10.20.30.40:8080 deleted.
```
*(Note: The exact success message may vary, or there might be no output if the command executes successfully and the entry is removed.)*

##  Field descriptions
This command does not produce tabular output.
*   On successful execution, it may display a confirmation message (as shown in the example above) or produce no output.
*   If the specified entry does not exist, it might indicate that the entry was not found or complete silently.
*   If arguments are missing or incorrectly formatted, it will typically display usage instructions or an error message.