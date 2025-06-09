#	--cpuset

##	Description
Displays the CPU set (cpuset) allocation for different processes on the VeloCloud Edge. This includes cores dedicated to dataplane (dp) processing, non-dataplane tasks (default), and Virtual Network Functions (VNF) if applicable. Understanding cpuset allocation can be useful for performance tuning and troubleshooting.

##  Arguments (optional)
| Argument | Description |
|---|---|
| none | This command does not take any arguments. |

##  Example usage
```
example_com:velocli> debug --cpuset
{
  "default_cpuset": 3,
  "dp_cpuset": 0,
  "vnf_cpuset": 1
}
```
##  Field descriptions
| Field | Description |
|---|---|
| `default_cpuset` | The set of CPU cores assigned to general system processes and non-dataplane tasks running on the Edge. The value is a bitmask representing the assigned cores (e.g., 3 (binary 0011) means cores 0 and 1 are assigned). |
| `dp_cpuset` | The set of CPU cores dedicated to dataplane processing. These cores handle packet forwarding, tunnel encapsulation/decapsulation, Quality of Service (QoS) enforcement, and other critical network functions. The value is a bitmask. |
| `vnf_cpuset` | The set of CPU cores allocated for Virtual Network Functions (VNFs) hosted on the Edge, such as third-party virtual firewalls. The value is a bitmask. This field may not be present or may be 0 if no VNFs are configured or running. |