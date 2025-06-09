#	--vnf

##	Description
Dumps information related to Virtual Network Functions (VNFs) configured or running on the VeloCloud Edge. VNFs are virtual appliances, such as third-party firewalls, that can be hosted on capable Edge hardware. This command provides details about the VNF's network configurations and status.

##  Arguments
This command takes no arguments.

##  Example usage
```
example_com:velocli> debug --vnf
{
  "networks": []
}
```

##  Field descriptions
The output is a JSON object with the following fields:

| Field      | Description                                                                                                |
|------------|------------------------------------------------------------------------------------------------------------|
| `networks` | An array of objects, where each object represents a network configured for or used by a VNF. If no VNFs are configured or active, or if they have no specific network configurations exposed through this command, this array may be empty. Each network object could contain details like network name, VLAN ID, IP addressing, and interfaces associated with the VNF. |