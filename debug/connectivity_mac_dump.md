#	--connectivity_mac_dump

##	Description
Shows entries in the connectivity MAC table. This table is used by the VeloCloud Edge to track MAC addresses learned on its LAN interfaces and their associated VLANs and segments. This information is crucial for Layer 2 switching and for determining how to forward traffic within the local network and into the SD-WAN overlay.

##  Arguments (optional)
| Argument | Description |
|---|---|
| none | This command takes no arguments. |

##  Example usage
The example below shows the output when the connectivity MAC table has not yet been initialized or is empty.
```
example_com:velocli> debug --connectivity_mac_dump
{
  "error": "Connectivity MAC table not initialized"
}

example_com:velocli>
```
A successful execution would typically show a table with columns such as MAC Address, VLAN ID, Segment ID, Interface, and potentially other flags or state information related to learned MAC entries.

##  Field descriptions
| Column | Description |
|---|---|
| N/A | The provided example shows an error message indicating the table is not initialized. A successful output would typically include fields like MAC Address, VLAN, Segment, Interface, and Age/Status. |