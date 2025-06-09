# --bgp_local_ip_dump [[all | prefix] [all | segment-id]]

## Description
Displays the list of BGP (Border Gateway Protocol) local IP addresses known to the VeloCloud Edge. These IP addresses are used by the BGP process on the Edge, for example, as source addresses for BGP peering sessions or as next-hop addresses in BGP advertisements. The list can be filtered by a specific IP prefix and/or by VeloCloud segment ID. BGP is a standard routing protocol used for exchanging routing information, often between the Edge and LAN-side routers, or between Edges and VeloCloud Gateways.

## Arguments (optional)
The command accepts up to two optional positional arguments. If no arguments are provided, it defaults to displaying all BGP local IPs for all segments.

| Argument Position | Parameter        | Description                                                                                                                                                              |
|-------------------|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1                 | `all` \| `prefix`  | Specifies the scope of BGP local IPs to display. <br> - `all`: Shows all BGP local IPs (this is the default if the argument is omitted). <br> - `prefix`: Provide an IP prefix (e.g., `192.168.10.0/24`) to filter the list and display only matching local IPs. |
| 2                 | `all` \| `segment-id` | Specifies the segment for which to display BGP local IPs. <br> - `all`: Shows BGP local IPs for all segments (this is the default if the argument is omitted or if the first argument is provided and this one is omitted). <br> - `segment-id`: Provide a numerical segment identifier to filter the list and display BGP local IPs associated with that specific segment. |

## Example usage
```
example_com:velocli> debug --bgp_local_ip_dump
```
*(The output for this specific command invocation is not detailed in the provided example. The command, when run, would list BGP local IP addresses based on the filters, if any, applied.)*

## Field descriptions
The specific fields outputted by this command are not detailed in the provided example. However, a typical output would include:
| Column             | Description                                                                 |
|--------------------|-----------------------------------------------------------------------------|
| Local IP Address   | The BGP local IP address.                                                   |
| Prefix Length      | The prefix length of the local IP address.                                  |
| Segment ID         | The segment ID with which this BGP local IP is associated.                  |
| Additional Flags/Info | Other relevant information or flags related to the BGP local IP (if any). |