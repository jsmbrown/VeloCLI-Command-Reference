#	--interfaces

##	Description
Shows the configured network interfaces on the VeloCloud Edge. This includes details about their IP addressing, VLAN tagging, operational mode, and association with network segments.

##  Arguments (optional)
This command takes no arguments.

##  Example usage
```json
example_com:velocli> debug --interfaces
[
  {
    "advertise": false,
    "ip_addr": "172.30.0.6",
    "ipv6_info": {
      "advertise": false
      // ... other ipv6_info fields like address, prefix_len, gateway, etc.
    },
    "netmask": "255.255.255.0",
    "vlan_id": 100,
    "interface": "GE3",
    "mac_addr": "00:50:56:01:02:03",
    "mode": "routed",
    "type": "LAN",
    "sub_interface_id": null,
    "mtu": 1500
    // ... many other configuration fields related to DHCP, OSPF, BGP, NAT, QoS, etc.
  }
  // ... additional interface objects may be listed if multiple interfaces are configured
]
```
**Note:** The example output above is a simplified snippet. The actual output is a JSON array where each object represents a configured interface and contains a comprehensive set of its configuration parameters.

##  Field descriptions
The command outputs a JSON array, where each object in the array represents a network interface. Common fields include:

| Field                 | Description                                                                                                                               |
|-----------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| `interface`           | The name of the physical or logical interface (e.g., "GE1", "GE2", "SFP1", "LAG0").                                                       |
| `type`                | The role of the interface, typically "WAN" or "LAN".                                                                                      |
| `mode`                | The operational mode of the interface, such as "routed", "switched", or "disabled".                                                       |
| `ip_addr`             | The IPv4 address configured on the interface. Empty if not configured.                                                                    |
| `netmask`             | The IPv4 subnet mask for the interface.                                                                                                   |
| `advertise`           | A boolean value. If `true`, the IPv4 network associated with this interface is advertised via routing protocols (e.g., OSPF, BGP) or into the VeloCloud overlay. |
| `ipv6_info`           | An object containing IPv6-specific configuration details.                                                                                 |
| `ipv6_info.address`   | The IPv6 address configured on the interface.                                                                                             |
| `ipv6_info.prefix_len`| The prefix length for the IPv6 address.                                                                                                   |
| `ipv6_info.gateway`   | The IPv6 gateway address for the interface.                                                                                               |
| `ipv6_info.advertise` | A boolean value. If `true`, the IPv6 network associated with this interface is advertised.                                                |
| `ipv6_info.dhcp_enabled`| Boolean indicating if DHCPv6 client is enabled for address assignment.                                                                  |
| `ipv6_info.slaac_enabled`| Boolean indicating if SLAAC (Stateless Address Autoconfiguration) is enabled for IPv6.                                                |
| `mac_addr`            | The MAC address of the interface.                                                                                                         |
| `vlan_id`             | The VLAN ID if the interface is configured as a VLAN subinterface or a switched port assigned to a specific VLAN. `null` or absent otherwise. |
| `sub_interface_id`    | Identifier for a sub-interface, if applicable.                                                                                            |
| `mtu`                 | The Maximum Transmission Unit (MTU) size in bytes for the interface.                                                                      |
| `nat_direct`          | Boolean indicating if NAT Direct (1:1 NAT for all ports to the interface's public IP) is enabled, typically for WAN interfaces.           |
| `wan_overlay`         | For WAN interfaces, a boolean indicating if this interface is used to build SD-WAN overlay tunnels.                                       |
| `segment_id`          | The numerical ID of the network segment to which this interface belongs.                                                                  |
| `segment_name`        | The name of the network segment.                                                                                                          |
| `dhcp_server_enabled` | For LAN interfaces, a boolean indicating if the DHCP server functionality is enabled on this interface.                                   |
| `ospf_enabled`        | Boolean indicating if OSPF is enabled on this interface.                                                                                  |
| `site_local_bgp_enabled` | Boolean indicating if BGP is enabled on this interface.                                                                                |
| ...                   | The output may contain many other fields detailing configurations for features such as QoS, port forwarding, static ARP, PPPoE, LLDP, CDP, VRRP, etc. |