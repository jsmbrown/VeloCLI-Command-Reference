#	--nht_regis_dump [[all | prefix] [all | segment-id] [all | v4 | v6]]

##	Description
This command dumps the Next Hop Tracker (NHT) registration list. The NHT is responsible for tracking the reachability of next-hop IP addresses, often learned via routing protocols like BGP or through static configuration, particularly for Non-VeloCloud Site (NVS) or Non-SD-WAN Destination (NSD) connectivity. This list shows registered next-hop IP addresses, their associated interfaces, and client protocols (like BGP or BFD) interested in their reachability status.

##  Arguments (optional)
| Argument | Description |
|---|---|
| `all` (default) | Display all NHT registrations. |
| `prefix` | Filter registrations by a specific IP prefix (e.g., 192.168.1.0/24). |
| `segment-id` | Filter registrations by a specific segment ID. If `all` is used, registrations across all segments are shown. |
| `v4` | Display only IPv4 registrations. |
| `v6` | Display only IPv6 registrations. |
| If no arguments are provided, it defaults to displaying all IPv4 and IPv6 registrations across all segments. | |

##  Example usage
```
example_com:velocli> debug --nht_regis_dump
Address                 Netmask                           Next Hop ID                         Dst LogicalId  Intf  Sub IntfId  Next Hop IP  Reachability  Clients  SEG
172.30.255.37   255.255.255.255  00000000-0000-0000-0000-000000000000  00000000-0000-0000-0000-000000000000   GE2         N/A   172.30.1.1             1        B    1
172.30.255.36   255.255.255.255  00000000-0000-0000-0000-000000000000  00000000-0000-0000-0000-000000000000   GE2         N/A   172.30.1.1             1        B    1
B - BGP, P - PIM, b - BFD
```

##  Field descriptions
| Column | Description |
|---|---|
| Address | The IP address of the registered next hop. |
| Netmask | The netmask associated with the next hop address. |
| Next Hop ID | A unique identifier for the next hop. This is often all zeros for non-VeloCloud destinations. |
| Dst LogicalId | The logical identifier of the destination. This is often all zeros for non-VeloCloud destinations. |
| Intf | The interface through which this next hop is reached (e.g., GE2). |
| Sub IntfId | The sub-interface ID, if applicable (N/A if not). |
| Next Hop IP | The IP address of the gateway or device that is the next hop. |
| Reachability | A status indicating if the next hop is currently reachable (1 for reachable, 0 for unreachable). |
| Clients | Client protocols registered for tracking this next hop's reachability. The legend for client flags is provided at the end of the command output (e.g., B - BGP, P - PIM, b - BFD). |
| SEG | The segment ID to which this next hop registration belongs. |