# --user_path_dump [all | Gateway | Edge Name/logical_id] [include_sub_path <0|1>] [show_only_hub_cluster_ic_tun <0|1>]

## Description
Dump VeloCloud Paths for Remote Diagnostics. This command provides information about the encrypted tunnels (paths) established by the VeloCloud Edge, which are fundamental to the SD-WAN overlay network. These paths can be to other Edges (spoke or hub) or to VeloCloud Gateways.

## Arguments (optional)
The command can be run without arguments to dump all paths with default options. The following optional arguments can be used to filter the output or include more details:

| Argument                                      | Description                                                                                                                                                                                                                               |
|-----------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `all`                                         | Specifies that paths to all remote systems (Edges and Gateways) should be dumped. This is often the default behavior if no specific target is provided.                                                                                   |
| `Gateway`                                     | Filters the dump to show only paths associated with VeloCloud Gateways.                                                                                                                                                                   |
| `Edge Name/logical_id`                        | Filters the dump to show paths related to a specific VeloCloud Edge. The Edge can be identified by its configured name (e.g., `BranchOffice1`) or its system logical ID (e.g., `velocloud-00001234-1234-1234-1234-123456789abc`).         |
| `include_sub_path <0|1>`                     | A keyword argument pair. If `include_sub_path 1` is specified, the output will include detailed information about the sub-paths (i.e., the individual WAN links and their characteristics that constitute a VeloCloud dynamic multi-path). If `0` is specified or the argument is omitted, these sub-path details are excluded (default is likely `0`). |
| `show_only_hub_cluster_ic_tun <0|1>`         | A keyword argument pair. If `show_only_hub_cluster_ic_tun 1` is specified, the output is filtered to display only those tunnels that are part of hub cluster interconnects (paths between hub Edges in a cluster). If `0` is specified or the argument is omitted, all relevant paths based on other filters are shown (default is likely `0`). |

## Example usage
To dump all VeloCloud paths with default verbosity:
```
example_com:velocli> debug --user_path_dump
```

To dump paths for a specific Edge named "BranchOffice1" and include sub-path details:
```
example_com:velocli> debug --user_path_dump BranchOffice1 include_sub_path 1
```

To dump paths related to VeloCloud Gateways, showing only hub cluster interconnect tunnels:
```
example_com:velocli> debug --user_path_dump Gateway show_only_hub_cluster_ic_tun 1
```

To dump all paths but explicitly request sub-path details:
```
example_com:velocli> debug --user_path_dump all include_sub_path 1
```

## Field descriptions
| Column | Description |
|---|---|
|   |  *Specific field descriptions for the output of this command are not available at this time. The output typically includes details about path state, performance metrics (latency, jitter, loss), tunnel encapsulation, and peer information.* |