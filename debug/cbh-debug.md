#	--cbh-debug

##	Description
This command displays debugging information related to Conditional Backhaul (CBH). CBH is a feature that allows the VeloCloud Edge to automatically backhaul internet-bound traffic to a hub Edge or VeloCloud Gateway if local internet links or all paths to a configured Cloud Security Service (CSS) are down. This command provides insights into the current state and timers associated with CBH decision-making.

##  Arguments (optional)
This command does not take any arguments.

##  Example usage
```
example_com:velocli> debug --cbh-debug
[
  {
    "backupLinkUp": 0,
    "conditionalBhHoldoff": 30000,
    "cssBackupPathsUp": 0,
    "cssPrimaryPathsUp": 1
  }
]
```

##  Field descriptions
| Field                  | Description                                                                                                |
|------------------------|------------------------------------------------------------------------------------------------------------|
| `backupLinkUp`         | Indicates if a backup WAN link is currently up and available. `0` means down, `1` means up.                |
| `conditionalBhHoldoff` | The hold-off timer in milliseconds. This is the duration the Edge will wait before initiating Conditional Backhaul after detecting a trigger condition (e.g., primary paths down). This helps prevent flapping. |
| `cssBackupPathsUp`     | The number of backup paths to the configured Cloud Security Service (CSS) that are currently operational.    |
| `cssPrimaryPathsUp`    | The number of primary paths to the configured Cloud Security Service (CSS) that are currently operational.   |
| 'pathToLocalGateway'   | The number of paths to the Local Gateway |
| 'privatePathToHub'     |  |
| 'publicAvailable'      |  |
| 'publicUptime'         |  |
| 'conditionalBhEnabled' |  |
| 'hubList'              |  |
| 'segId'                |  |
  
