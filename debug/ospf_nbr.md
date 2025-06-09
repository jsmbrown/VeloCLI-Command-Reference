# `debug --ospf_nbr [v4 | v6 | all]`

## Description
Displays the status and details of Open Shortest Path First (OSPF) protocol neighbors for the VeloCloud Edge. This command can filter neighbors by address family (IPv4 or IPv6). If OSPF is not configured or enabled on the Edge for a specific address family, the command will indicate this status.

OSPF is a dynamic routing protocol used to exchange routing information within an autonomous system. VeloCloud Edges can participate in OSPF adjacencies to learn and advertise routes with other OSPF-speaking routers on the LAN side.

## Arguments (optional)
| Argument      | Description                                                                                                |
|---------------|------------------------------------------------------------------------------------------------------------|
| `v4`          | Displays OSPF neighbors specifically for the IPv4 address family.                                            |
| `v6`          | Displays OSPF neighbors specifically for the IPv6 address family.                                            |
| `all`         | Displays OSPF neighbors for both IPv4 and IPv6 address families.                                             |
| (no argument) | Defaults to `all`, displaying OSPF neighbors for both IPv4 and IPv6 address families.                        |

## Example usage
```
example_com:velocli> debug --ospf_nbr
IPv4 Neighbors
==============
OSPF is not enabled

IPv6 Neighbors
==============
```
*(Note: The example above shows output when OSPF is not enabled. If OSPF were active with established neighbors, the output would list neighbor details under the respective IPv4 or IPv6 sections.)*

## Field descriptions
The output format and fields displayed depend on whether OSPF is enabled and if any neighbors are established.

If OSPF is not enabled for an address family, a message similar to "OSPF is not enabled" will be shown under the respective section (IPv4 Neighbors or IPv6 Neighbors).

If OSPF is enabled and neighbors are present, the output will typically include the following details for each neighbor:

| Column        | Description                                                                    |
|---------------|--------------------------------------------------------------------------------|
| Neighbor ID   | The OSPF Router ID of the neighboring router.                                  |
| Pri           | The OSPF priority of the neighbor's interface.                                 |
| State         | The current state of the OSPF adjacency (e.g., FULL, 2WAY, INIT).              |
| Dead Time     | The time remaining before the neighbor is declared down if no Hello packets are received. |
| Address       | The IP address of the neighbor's interface to which this Edge is connected.    |
| Interface     | The local Edge interface through which the OSPF adjacency is formed.           |
| Uptime        | The duration for which the OSPF adjacency has been established.                |
| Options       | OSPF options supported by the neighbor.                                        |
| DR            | Designated Router on the network segment.                                      |
| BDR           | Backup Designated Router on the network segment.                               |

*(The exact column names and information might vary slightly based on the specific software version and OSPF configuration.)*