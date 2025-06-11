#	--bw_retest

##	Description
This command initiates a bandwidth retest on all WAN interfaces of the VeloCloud Edge. This is useful for situations where link conditions may have changed and an updated bandwidth measurement is desired for optimal path selection and Quality of Experience (QoE) management.

##  Arguments (optional)
| Argument | Description |
|---|---|
| none | This command does not accept any arguments. |

##  Example usage
```
example_com:velocli> debug --bw_retest
{
  "bw_retest": "test in progress"
}

example_com:velocli>
```

##  Field descriptions
| Field | Description |
|---|---|
| bw_retest | Indicates the status of the bandwidth retest. "test in progress" signifies that the bandwidth measurement process has been initiated on the interfaces. |