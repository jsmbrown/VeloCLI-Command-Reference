#	--verbose_routes [[all | prefix] [all | segment-id] [v4 | v6 | all]]

##	Description
Dumps the unified VeloCloud route table in a raw, unformatted JSON structure. This provides detailed information about each route known by the VeloCloud Edge, similar to `debug --routes` but in a machine-readable format. This output is useful for scripting or detailed analysis of the routing state.

##  Arguments (optional)
The arguments are positional. If an earlier argument is specified, all preceding arguments must also be specified (e.g., using 'all' if a default behavior is desired for a preceding argument).

| Argument | Description |
|---|---|
| `prefix` | (Optional) First positional argument. Specifies an IP prefix (e.g., `192.168.1.0/24` or `2001:db8::/32`) to filter the route table. Use 'all' or omit this argument (if no subsequent arguments are provided) to display routes for all prefixes. |
| `segment-id` | (Optional) Second positional argument. Specifies the segment ID (an integer) to filter the route table. Use 'all' or omit this argument (if no subsequent arguments are provided) to display routes for all segments. Segments are used for network segmentation within the SD-WAN fabric. |
| `v4 \| v6 \| all` | (Optional) Third positional argument. Specifies the IP version of the routes to display. Options are `v4` for IPv4 routes, `v6` for IPv6 routes, or `all` for both. Defaults to `all` if omitted. |

##  Example usage
To dump all routes for all segments and IP versions in JSON format:
```
example_com:velocli> debug --verbose_routes
{
  "routes": [
    {
      "addr": "192.168.88.1",
      "netmask": "255.255.255.255",
      "gateway_ip": "0.0.0.0",
      "flags": "C",
      "preference": 0,
      "cost": 0,
      "protocol": "connected",
      "type": "connected",
      "interface": "GE3",
      "vlan": 0,
      "segment_id": 1,
      "is_reachable": true,
      "age_s": 161537,
      "arp_src": "0.0.0.0",
      "mtu": 1500
      // ... additional route fields may be present depending on the route type
    },
    {
      "addr": "0.0.0.0",
      "netmask": "0.0.0.0",
      "gateway_ip": "169.254.0.1",
      "flags": "S",
      "preference": 10,
      "cost": 0,
      "protocol": "static",
      "type": "gateway",
      "interface": "INTERNET_GE1",
      "segment_id": 0,
      "is_reachable": true,
      "dest_logical_id": "gateway-00000001",
      "next_hop_id": "gateway-00000001",
      "next_hop_name": "VCG1-AWS",
      "next_hop_ip": "169.254.0.1",
      "mtu": 1360
      // ... additional route fields
    }
    // ... more route objects
  ]
}
```
To dump only IPv4 routes for prefix `10.0.0.0/8` in segment `1`:
```
example_com:velocli> debug --verbose_routes 10.0.0.0/8 1 v4
```

##  Field descriptions
The command outputs a JSON object. The primary key is `routes`, which contains an array of route objects. Each route object represents a single route entry and can have numerous fields. The presence of specific fields can vary depending on the route type (e.g., connected, static, BGP, OSPF, VCRP overlay route). Below are common fields found within each route object:

| JSON Key (within each route object) | Description |
|---|---|
| `addr` | The destination IP address or prefix for the route. |
| `netmask` | The netmask for the destination prefix. |
| `gateway_ip` | The IP address of the next-hop gateway for underlay routes, or an overlay identifier. |
| `flags` | A string or numerical value representing flags that indicate the state or properties of the route (e.g., Connected, Static, BGP, Overlay, Reachable). The interpretation may require VeloCloud-specific knowledge or comparison with the legend from the `debug --routes` command. |
| `preference` | The administrative distance or preference value for the route. Lower values are generally preferred when multiple routes to the same destination exist from different protocols. |
| `cost` / `metric` | The metric or cost associated with the route, used by routing protocols to determine the best path. |
| `protocol` | The routing protocol or source from which the route was learned (e.g., `connected`, `static`, `bgp`, `ospf`, `vcrp`). |
| `type` | The VeloCloud-specific type of route (e.g., `connected`, `static`, `bgpLocal`, `bgpOverlay`, `ospfExternal`, `edge2edge`, `hub`, `gateway`, `nonVelocloudSite`). |
| `interface` | The logical or physical interface through which this route is reachable (e.g., `GE1`, `LAN1`, `TUN0`, `VNI-EDGE-1234`). |
| `vlan` | The VLAN ID associated with the route, if applicable (typically for LAN-side routes). |
| `segment_id` | The ID of the segment to which this route belongs. `0` often refers to the global segment or underlay-facing segment. |
| `is_reachable` | Boolean (`true` or `false`) indicating if the route is currently considered active and reachable. |
| `age_s` | The age of the route entry in seconds since it was learned or last refreshed. |
| `arp_src` | The source IP address used in ARP resolution for this route, typically relevant for LAN-learned routes. |
| `mtu` | Maximum Transmission Unit for the path associated with this route. |
| `dest_logical_id` | For overlay routes, the logical ID (e.g., a UUID or named identifier) of the destination VeloCloud Edge, Hub, or Gateway. |
| `next_hop_id` | For overlay routes, the logical ID of the immediate next-hop VeloCloud device (Edge or Gateway) in the SD-WAN fabric. |
| `next_hop_name` | The configured name of the next-hop VeloCloud device. |
| `next_hop_ip` | The IP address of the next hop, which could be an underlay IP or an overlay tunnel endpoint IP. |
| `bgp_as_path` | (If BGP route) The BGP AS path attribute. |
| `bgp_local_pref` | (If BGP route) The BGP local preference attribute. |
| `bgp_med` | (If BGP route) The BGP Multi-Exit Discriminator (MED) attribute. |
| `ospf_route_type` | (If OSPF route) The OSPF route type (e.g., Intra-area, Inter-area, External Type 1/2). |
| *... and others* | The output can be very verbose and include many other internal state, diagnostic, QoE, and VeloCloud-specific fields depending on the route's nature and system configuration. |