#	--stale_pi_dump

##	Description
This command dumps a list of stale Path Information (PI) entries. Stale PI refers to path data that is no longer current or considered valid by the VeloCloud Edge. This can be useful for troubleshooting issues related to path selection, tunnel formation, or outdated routing information within the SD-WAN overlay.

##  Arguments
This command takes no arguments.

##  Example usage
```
example_com:velocli> debug --stale_pi_dump
PI   PEER LOGICAL ID  PEER TYPE  OBJ STATE  REF OBJS  DURATION

example_com:velocli>
```

##  Field descriptions
| Column          | Description                                                                 |
|-----------------|-----------------------------------------------------------------------------|
| PI              | Identifier for the Path Information entry.                                  |
| PEER LOGICAL ID | The unique logical identifier of the peer (e.g., another Edge or Gateway).  |
| PEER TYPE       | The type of the peer associated with this path information.                 |
| OBJ STATE       | The current state of the Path Information object.                           |
| REF OBJS        | Reference objects or count related to this PI entry.                        |
| DURATION        | The duration for which this Path Information entry has been considered stale. |