#	--gateways

##	Description
Dumps the current list of VeloCloud Gateways assigned to the Edge. This list includes operational status and configuration details for each gateway.

##  Arguments (optional)
| Argument | Description |
|---|---|
| none | This command does not take any arguments. |

##  Example usage
```json
example_com:velocli> debug --gateways
[
  {
    "CDE Enabled": false,
    "Controller": false,
    "IPSec gateway IP Addr": "N/A",
    "Local Gateway": true,
    "LogicalId": "0f3451eb-f740-4c9f-8767-ff28eddcba58",
    "Name": "vcg32-sjc1",
    "Peer State": "ALIVE",
    "Primary Global GW": true,
    "Private IP Address": "N/A",
    "Private IPv6 Address": "::",
    "Public IP Address": "216.221.25.32",
    "Public IPv6 Address": "2605:a7c0:0:301::32",
    "State": "ACTIVE",
    "Type": "Public",
    "cws capable": false,
    "cws primary gateway": false,
    "epType": 16,
    "onPremise": "No",
    "private_network_id": 0,
    "super_alt_gw": false,
    "super_gw": false,
    "wss capable": false,
    "wss primary gateway": false
  },
  {
    "CDE Enabled": false,
    "Controller": false,
    "IPSec gateway IP Addr": "N/A",
    "Local Gateway": false,
    "LogicalId": "e8c36645-6864-42a3-8ee1-c6792e92febf",
    "Name": "vcg1ip6-usor1",
    "Peer State": "ALIVE",
    "Primary Global GW": false,
    "Private IP Address": "N/A",
    "Private IPv6 Address": "::",
    "Public IP Address": "34.209.79.189",
    "Public IPv6 Address": "2600:1f13:d18:ca01:aac1:908b:e411:674b",
    "State": "ACTIVE",
    "Type": "Public",
    "cws capable": false,
    "cws primary gateway": false,
    "epType": 16,
    "onPremise": "No",
    "private_network_id": 0,
    "super_alt_gw": true,
    "super_gw": false,
    "wss capable": false,
    "wss primary gateway": false
  }
]
```

##  Field descriptions
The command outputs a JSON array, where each object represents a VeloCloud Gateway and contains several key-value pairs. The following are commonly observed fields:

| Field                   | Description |
|-------------------------|-------------|
| `CDE Enabled`           | Indicates if a gateway is designated as part of the PCI certified SD-WAN service and is eligible to handle traffic for cardholder data environment (CDE) segments. |
| `Controller`            | If `true`, this VeloCloud Gateway also performs control plane functions, acting as a VeloCloud Controller. |
| `IPSec gateway IP Addr` | String. The IP address used by the gateway for IPSec tunnel termination with other sites (e.g., Non-VeloCloud Sites or Edges). Displays "N/A" if not applicable or not configured. |
| `Local Gateway`         | If `true`, this gateway is designated as the primary gateway for the Edge from which the command is run. |
| `LogicalId`             | UUID assigned to the VeloCloud Gateway. |
| `Name`                  | The configured name of the VeloCloud Gateway. |
| `Peer State`            | Status of connectivity to the VeloCloud Gateway. |
| `Private IP Address`    | If present, IPv4 address assigned to the handoff interface on a Partner Gateway. |
| `Private IPv6 Address`  | If present, IPv6 address assigned to the handoff interface on a Partner Gateway. |
| `Public IP Address`     | IPv4 address assigned to the public interface on the VeloCloud Gateway. |
| `Public IPv6 Address`   | If present, IPv6 address assigned to the public interface on the VeloCloud Gateway. |
| `State`                 | Operational state of the VeloCloud Gateway. |
| `Type`                  | Indicates the gateway role (i.e. "Public" for Cloud Gateway, "Private" for Partner Gateway). |
| `cws capable`           | Deprecated |
| `cws primary gateway`   | Deprecated |
| `onPremise`             | If "No", indicates that the gateway is deployed in a VeloCloud PoP. |
| `super_alt_gw`          | If `true`, this VeloCloud Gateway is designated as the alternate super gateway for the overlay. |
| `super_gw`              | If `true`, this VeloCloud Gateway is designated as the super gateway for the overlay. |
| `wss capable`           | If `true`, this gateway is capable of PoP to PoP connectivity to VeloCloud Cloud Web Security Services |
| `wss primary gateway`   | If `true`, this gateway is assigned to be used as PoP to PoP connectivity for dataplane traffic to |