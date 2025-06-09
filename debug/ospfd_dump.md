#	--ospfd_dump [v4 | v6 | all] [seg | all]

##	Description
Shows the status of the OSPFv2 (ospfd) and/or OSPFv3 (ospf6d) routing protocol daemon database. This can include information about neighbors, link states, and overall OSPF process health within different network segments.

##  Arguments (optional)
The command accepts up to two optional positional arguments. If arguments are provided, they must appear in the order listed.

| Argument Value    | Applies to        | Description                                                                                                |
|-------------------|-------------------|------------------------------------------------------------------------------------------------------------|
| `v4`              | IP Version (1st)  | Display OSPFv2 (IPv4) database status.                                                                     |
| `v6`              | IP Version (1st)  | Display OSPFv3 (IPv6) database status.                                                                     |
| `all`             | IP Version (1st)  | Display for both OSPFv2 (IPv4) and OSPFv3 (IPv6). This is the default if no IP version argument is specified.                  |
| `seg`             | Segment Filter (2nd)| Display OSPF database status with a focus on segment-specific details or grouped by segment.               |
| `all`             | Segment Filter (2nd)| Display OSPF database status for all segments or without a specific segment focus. This is the default if no segment filter argument is specified. |

**Notes on argument usage:**
*   If no arguments are provided, `debug --ospfd_dump` defaults to showing information for `all` IP versions and `all` segments (equivalent to `debug --ospfd_dump all all`).
*   If only one argument is provided, it is interpreted as the IP Version filter (e.g., `debug --ospfd_dump v4` is equivalent to `debug --ospfd_dump v4 all`).
*   To specify the Segment Filter (the second argument, e.g., `seg`), the IP Version filter (the first argument) must also be provided (e.g., `debug --ospfd_dump all seg`).

##  Example usage
```
example_com:velocli> debug --ospfd_dump
```
This example runs the command without any arguments, which will typically display the OSPF database status for all IP versions (IPv4 and IPv6) and across all relevant segments.

##  Field descriptions
| Column | Description |
|---|---|
|   |  *Specific output fields for this command depend on the arguments used and the current OSPF state. Detailed field descriptions are not available without example output.* |