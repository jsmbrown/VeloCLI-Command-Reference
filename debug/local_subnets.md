#	--local_subnets

##	Description
This command displays the subnets that are locally configured on the VeloCloud Edge. These are typically networks connected to the LAN interfaces of the Edge and advertised into the SD-WAN overlay.

##  Arguments (optional)
This command does not take any arguments.

##  Example usage
```
example_com:velocli> debug --local_subnets
Address              Netmask  Interface  Secure
169.254.99.0   255.255.255.0  network_1       1
```

##  Field descriptions
| Column    | Description                                                                 |
|-----------|-----------------------------------------------------------------------------|
| Address   | The network address of the local subnet.                                    |
| Netmask   | The subnet mask for the local network.                                      |
| Interface | The logical interface on the Edge to which this subnet is associated.       |
| Secure    | Indicates if the subnet is considered secure (1 for yes, 0 for no). This often relates to whether traffic from this subnet can be sent over secure VeloCloud paths. |