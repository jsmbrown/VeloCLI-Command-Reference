#	--mode_link

##	Description
Displays information about Backup/Hot Standby link configurations on the VeloCloud Edge. This includes whether a backup link is currently active, the name of the designated hot standby link, and the minimum number of active links required before a backup link would be activated.

##  Arguments (optional)
| Argument | Description |
|---|---|
| none | This command does not take any arguments. |

##  Example usage
```
example_com:velocli> debug --mode_link
{
  "backupHsbyActive": 0,
  "backupHsbylinkname": "N/A",
  "minActiveLinks": 1
}
```
##  Field descriptions
| Field | Description |
|---|---|
| backupHsbyActive | Indicates if a backup hot standby link is currently active. `0` means inactive, `1` means active. |
| backupHsbylinkname | The name of the link designated as the hot standby. "N/A" if no specific link is configured or active as hot standby. |
| minActiveLinks | The minimum number of primary links that must be active. If the number of active primary links falls below this threshold, the hot standby link (if configured and available) will be activated. |