# --pmtud_run [all | peer_name | td_version | interface]

## Description
Force Path MTU Discovery (PMTUD) on overlay paths. This command helps determine the optimal MTU size for paths to ensure efficient data transmission and avoid fragmentation. By default, it probes all active paths, but can be targeted to specific paths using the optional arguments.

## Arguments (optional)
The command accepts one optional argument to specify the scope of the PMTUD operation. If no argument is provided, it defaults to `all`.

| Argument     | Description                                                                                                                               |
|--------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| `all`        | Force PMTUD on all established overlay paths. This is the default behavior if no specific argument is provided.                             |
| `peer_name`  | Force PMTUD only on paths to the specified peer. The `peer_name` should be the name of a remote VeloCloud Edge or Gateway.                  |
| `td_version` | Force PMTUD only on paths associated with the specified tunnel discovery version. Common values include `v4` (for IPv4) or `v6` (for IPv6). |
| `interface`  | Force PMTUD only on paths that utilize the specified WAN interface (e.g., `GE1`, `GE2`, `PPPoE1`).                                          |

## Example usage
The following example shows the command being run when no active paths are available for PMTUD:
```
example_com:velocli> debug --pmtud_run
{
  "Error": "No Paths Found"
}

example_com:velocli>
```
If paths were available, the command would initiate PMTUD on them. Successful execution typically does not produce direct output to the console but triggers background PMTUD processes. The results of PMTUD can be observed in path statistics or logs.

## Field descriptions
The command output is in JSON format.

| Field   | Description                                                                                                                               |
|---------|-------------------------------------------------------------------------------------------------------------------------------------------|
| `Error` | A string describing an error if the command could not be executed as intended. For instance, "No Paths Found" indicates no active overlay paths were available for PMTUD at the time of execution. |