#	--get_vnf_ha_state

##	Description
Obtains the current VNF HA (Virtual Network Function High Availability) state on the VeloCloud Edge. VNF refers to virtualized network services, such as firewalls, that can run on the Edge appliance. This command helps determine if the HA mechanism for these VNFs is currently active.

##  Arguments (optional)
| Argument | Description |
|---|---|
| none | This command does not take any arguments. |

##  Example usage
```
example_com:velocli> debug --get_vnf_ha_state
{
  "is_vnf_ha_active": 0
}
```

##  Field descriptions
| Field | Description |
|---|---|
| is_vnf_ha_active | Indicates the current High Availability state for Virtual Network Functions (VNFs) on the Edge. <br> `0`: VNF HA is inactive. <br> `1`: VNF HA is active. |