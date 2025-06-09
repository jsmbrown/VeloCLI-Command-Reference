# `debug --list_vpn_endpoints`

## Description
Dumps the list of endpoints available for VPN Testing. These endpoints typically include VeloCloud Gateways and Hub Edges that the current Edge can form VPN tunnels with. This command is useful for troubleshooting VPN connectivity and verifying the available paths for VPN tests initiated from the Edge.

## Arguments
This command does not take any arguments.

## Example Usage
```
example_com:velocli> debug --list_vpn_endpoints
usage: debug.py [-h] [--mode_link] [--timeout TIMEOUT SECONDS]
                [--logfile LOGFILE] [--limit N] [-v]
                [--biz_pol_dump [[all | segment-id] [[all | policy-name]
                ...]]] [--netflow_intervals] [--netflow_collectors]
                [--netflow_filters [<collector_id>]] [--bw_testing_dump]
                [--chat_stats [[sip=] [dip=] [dport=] [app_id=]
```
**Note:** The output shown in the example above is the general help text for the `debug.py` script. The actual output of `debug --list_vpn_endpoints` will be a list of VPN endpoints, detailing their names, IP addresses, and potentially other relevant information for establishing VPN connections.

## Field Descriptions
The actual output of this command will list VPN endpoints. While the exact fields may vary, typical information includes:
| Column/Field      | Description                                                                 |
|-------------------|-----------------------------------------------------------------------------|
| Endpoint Name     | The configured name of the VPN endpoint (e.g., Gateway name, Hub Edge name). |
| IP Address        | The IP address of the VPN endpoint.                                         |
| Type              | The type of endpoint (e.g., Gateway, Hub).                                  |
| Reachability      | Status indicating if the endpoint is currently reachable.                   |
| Other Information | Additional details relevant to VPN connectivity or testing.                 |