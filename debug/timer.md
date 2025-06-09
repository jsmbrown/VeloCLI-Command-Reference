#	--timer

##	Description
Dumps the current state of the internal timer wheels used by the VeloCloud Edge software. Timer wheels are data structures used for efficiently managing and triggering timed events. This command provides insights into the operational status and workload of these timers.

##  Arguments (optional)
| Argument | Description |
|---|---|
| none | This command takes no arguments. |

##  Example usage
```
example_com:velocli> debug --timer
[
  {
    "calculatedUsers": 38,
    "name": "slow_wheel0",
    "runState": 1,
    "taskExecCnt": 33726,
    "taskInsertCnt": 33726,
    "taskRemoveCnt": 0,
    "tick": 1678208,
    "users": 38
  },
  {
    "calculatedUsers": 1,
    "name": "fast_wheel0",
    "runState": 1,
    "taskExecCnt": 0,
    "taskInsertCnt": 0,
    "taskRemoveCnt": 0,
    "tick": 1678208,
    "users": 1
  }
]
```

##  Field descriptions
The output is a JSON array, where each object represents a timer wheel and contains the following fields:

| Field             | Description                                                                 |
|-------------------|-----------------------------------------------------------------------------|
| `calculatedUsers` | The number of users or tasks calculated to be managed by this timer wheel.  |
| `name`            | The name of the timer wheel (e.g., "slow_wheel0", "fast_wheel0").           |
| `runState`        | The current operational state of the timer wheel (e.g., 1 for running).     |
| `taskExecCnt`     | The total count of tasks that have been executed by this timer wheel.       |
| `taskInsertCnt`   | The total count of tasks that have been inserted into this timer wheel.     |
| `taskRemoveCnt`   | The total count of tasks that have been removed from this timer wheel.      |
| `tick`            | The current tick count of the timer wheel, representing its progression.    |
| `users`           | The current number of users or tasks registered with this timer wheel.      |