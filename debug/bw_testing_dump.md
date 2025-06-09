#	--bw_testing_dump

##	Description
This command dumps the current bandwidth test data. Bandwidth testing is a crucial component of the VeloCloud SD-WAN solution, used to assess the capacity and quality of underlying WAN links. This information is utilized by the VeloCloud Orchestrator and Edges for path selection, Quality of Experience (QoE) calculations, and Dynamic Multipath Optimization (DMPO) decisions.

##  Arguments (optional)
| Argument | Description |
|---|---|
| none | This command does not take any arguments. |

##  Example usage
```
example_com:velocli> debug --bw_testing_dump
[]

example_com:velocli>
```
##  Field descriptions
| Column | Description |
|---|---|
| N/A | The example output `[]` indicates that there is currently no bandwidth test data to display or that the data structure is empty. When data is present, it would typically include details about ongoing or completed bandwidth tests on various paths. |