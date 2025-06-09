#	--uptime

##	Description
Displays the uptime of the VeloCloud Edge's main process. This indicates how long the core SD-WAN service has been running since its last restart or initialization.

##  Arguments (optional)
| Argument | Description |
|---|---|
| none | This command does not take any arguments. |

##  Example usage
```
example_com:velocli> debug --uptime
Uptime: 01:43:17, 0 days
Start: 66106, Current: 6263777
```

##  Field descriptions
| Column | Description |
|---|---|
| Uptime | The duration the VeloCloud Edge process has been running, displayed in HH:MM:SS format and also in the total number of days. |
| Start | An internal counter or timestamp indicating when the process started. |
| Current | An internal counter or timestamp indicating the current time of the query, used in conjunction with 'Start' to calculate uptime. |