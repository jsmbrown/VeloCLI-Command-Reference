#	--cos

##	Description
Displays the Classes of Service (CoS) queues for each interface on the VeloCloud Edge. This includes details about DSCP (Differentiated Services Code Point) tags, bandwidth allocation, and whether a CoS is the default for an interface.

##  Arguments (optional)
| Argument | Description |
|---|---|
| none | This command takes no arguments. |

##  Example usage
```
example_com:velocli> debug --cos
Interface   |  CoS Name  |   DSCPTags  |  BwPct  |  Bw_Upperlimit  |  DefaultCoS
GE1         |  Priority  |         EF  |     20  |            YES  |          NO
GE1         |      Bulk  |  CS0, AF11  |     80  |             NO  |         YES
```

##  Field descriptions
| Column | Description |
|---|---|
| Interface | The physical or logical interface on the Edge to which the Class of Service policy is applied (e.g., GE1, GE2). |
| CoS Name | The user-defined name for the Class of Service (e.g., Priority, Bulk). |
| DSCPTags | The Differentiated Services Code Point (DSCP) values associated with this Class of Service. Traffic marked with these DSCP values will be treated according to this CoS policy. |
| BwPct | The percentage of the interface's available bandwidth guaranteed to this Class of Service. |
| Bw_Upperlimit | Indicates whether there is a hard upper limit on the bandwidth this Class of Service can consume. 'YES' means it cannot exceed the allocated BwPct, even if spare bandwidth is available. 'NO' means it can potentially use more than its allocated BwPct if other classes are not fully utilizing their share. |
| DefaultCoS | Indicates if this Class of Service is the default for traffic on this interface that does not match any other specific CoS rule. 'YES' means it is the default; 'NO' means it is not. |