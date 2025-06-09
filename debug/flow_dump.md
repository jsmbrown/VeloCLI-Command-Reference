# --flow_dump {local | all | logical-id <ID>} {all | <dest-ip>} {all | <segid>} [all | v4 | v6]

## Description
Dump the current flow table entries on the VeloCloud Edge. This command provides a snapshot of active traffic sessions, including details about their path through the SD-WAN overlay, applied policies (like QoS and NAT), and performance characteristics. This information is crucial for troubleshooting connectivity, performance issues, and verifying policy enforcement.

## Arguments
The command requires a specific set of arguments to filter the flow dump. The structure depends on the first argument chosen.

| Parameter             | Choices / Value                               | Description                                                                                                                                                              |
|-----------------------|-----------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `flow_scope`          | `local`                                       | Display flows originating from or terminating on the VeloCloud Edge itself (e.g., management traffic, BGP sessions).                                                     |
|                       | `all`                                         | Display all flows known to the Edge, including transit traffic.                                                                                                          |
|                       | `logical-id <ID>`                             | Display flows associated with a specific remote VeloCloud peer (another Edge or a Gateway). `<ID>` is the unique logical identifier of the peer and must be provided as the argument immediately following `logical-id`. |
| `destination_filter`  | `all`                                         | Do not filter by destination IP address.                                                                                                                                 |
|                       | `<dest-ip>`                                   | Filter flows by the specified destination IP address (e.g., `192.168.1.100`).                                                                                             |
| `segment_filter`      | `all`                                         | Do not filter by segment ID. Flows from all segments will be displayed.                                                                                                  |
|                       | `<segid>`                                     | Filter flows by the specified segment ID (e.g., `0`, `1`). Segments are used for network segmentation within the VeloCloud SD-WAN.                                        |
| `ip_version` (Optional) | `all`                                         | Display both IPv4 and IPv6 flows. This is the default if the argument is omitted.                                                                                        |
|                       | `v4`                                          | Display only IPv4 flows.                                                                                                                                                 |
|                       | `v6`                                          | Display only IPv6 flows.                                                                                                                                                 |

**Argument Order and Requirements:**
The command expects arguments in the following order:
1.  `flow_scope`: One of `local`, `all`, or `logical-id`.
    *   If `logical-id` is chosen, the next argument *must* be the `<ID>` of the peer.
2.  `destination_filter`: Either `all` or a specific `<dest-ip>`.
3.  `segment_filter`: Either `all` or a specific `<segid>`.
4.  `ip_version` (Optional): `all`, `v4`, or `v6`.

A minimum of three arguments are required if `flow_scope` is `local` or `all`. If `flow_scope` is `logical-id`, then `<ID>` is also required, effectively making it four mandatory arguments followed by the optional IP version.

## Example Usage
**Incorrect Usage (Insufficient Arguments):**
```
example_com:velocli> debug --flow_dump
Insufficient Arguments provided. Minimum number of argument is 3.
                  usage: --flow_dump [local | logical-id | all] [all | dest-ip] [all | segid]
```

**Correct Usage Examples:**
1.  Dump all flows (IPv4 and IPv6) across all segments, without filtering by destination IP:
    ```
    example_com:velocli> debug --flow_dump all all all
    ```
2.  Dump local IPv4 flows destined for IP `172.16.10.5` on segment `1`:
    ```
    example_com:velocli> debug --flow_dump local 172.16.10.5 1 v4
    ```
3.  Dump IPv6 flows related to the peer with logical ID `3294602a-5a69-4694-a7d2-811aff737faa`, for any destination IP, on any segment (typically segment `0` for peer-specific flows if not otherwise specified by policy):
    ```
    example_com:velocli> debug --flow_dump logical-id 3294602a-5a69-4694-a7d2-811aff737faa all all v6
    ```

**(Note:** The actual output of `debug --flow_dump` is extensive and tabular, detailing numerous aspects of each flow. The specific columns and their exact names can vary. See Field Descriptions below for common information elements.)

## Field Descriptions
The output of `debug --flow_dump` is a detailed table where each row represents a flow. The columns provide information about various aspects of the flow. While the exact column names and order may vary, common fields include:

| Column (Typical)      | Description                                                                                                |
|-----------------------|------------------------------------------------------------------------------------------------------------|
| `SrcIP` / `Src Addr`  | Source IP address of the flow.                                                                             |
| `SrcPort` / `Src Pt`  | Source port number (for TCP/UDP).                                                                          |
| `DstIP` / `Dst Addr`  | Destination IP address of the flow.                                                                        |
| `DstPort` / `Dst Pt`  | Destination port number (for TCP/UDP).                                                                     |
| `Proto`               | Protocol number or name (e.g., TCP, UDP, ICMP).                                                            |
| `Segment` / `SegID`   | The segment ID associated with the flow.                                                                   |
| `IngressIf` / `InIF`  | Ingress interface or link identifier where the flow entered the Edge.                                      |
| `EgressIf` / `OutIF`  | Egress interface, path, or tunnel identifier used by the flow leaving the Edge.                            |
| `PathId` / `TunnelId` | Identifier for the VeloCloud SD-WAN path or tunnel carrying the flow.                                      |
| `Application` / `AppId`| Application ID or name identified by deep packet inspection (DPI).                                         |
| `DSCP`                | Differentiated Services Code Point value, indicating QoS marking.                                          |
| `NAT Info`            | Information about Network Address Translation applied (e.g., NAT source IP/port).                          |
| `State`               | Current state of the flow (e.g., `ESTABLISHED`, `NEW`, `CLOSED`).                                          |
| `Packets (Fwd/Rev)`   | Packet count in the forward (source to destination) and reverse (destination to source) directions.        |
| `Bytes (Fwd/Rev)`     | Byte count in the forward and reverse directions.                                                          |
| `FlowCreateTime`      | Timestamp when the flow was first seen or created.                                                         |
| `LastPacketTime`      | Timestamp of the last packet seen for this flow.                                                           |
| `QoE Status`          | Quality of Experience metrics or status, if applicable.                                                    |
| `DEC Applied`         | Indicates if Dynamic Multipath Optimization (DMPO) / Dynamic Error Correction (DEC) actions were applied.  |
| `PolicyId` / `RuleId` | Identifier of the business policy rule or firewall rule that matched this flow.                            |
| `Flags`               | Various flags indicating flow properties or treatments.                                                    |

The output provides a comprehensive view of traffic handling, essential for diagnosing network behavior and verifying configurations within the VeloCloud SD-WAN fabric.