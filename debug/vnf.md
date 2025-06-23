#	--vnf

##	Description
Dumps information related to Virtual Network Functions (VNFs) configured or running on the VeloCloud Edge. VNFs are virtual appliances, such as third-party firewalls, that can be hosted on capable Edge hardware. This command provides details about the VNF's network configurations and status.

##  Arguments
This command takes no arguments.

##  Example usage
```
example_com:velocli> debug --vnf
{
  "networks": [
    {
      "down": 0, 
      "mac": "f0:8e:db:dd:00:00", 
      "name": "sfp1", 
      "tag": 0, 
      "vlan": 0
    }
  ]
}
```

##  Field descriptions
The output is a JSON object with the following fields:

| Field      | Description                                                                                                |
|------------|------------------------------------------------------------------------------------------------------------|
| `networks` | An array of objects, where each object represents a LAN interface or VLAN configured for VNF insertion. |
| `down` | Interface/VLAN operational status with `0` indicating that the network is up, or `1` if the network is down. |
| `mac` | MAC address of the interface/VLAN |
| `name` | Logical name of the interface/VLAN |
| `tag` | 802.1Q tag (`0` if untagged) |
| `VLAN` | VLAN ID (`0` for routed interfaces) |