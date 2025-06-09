# --ike_delete_p1_sa `[peer_ip]` `[cookie]`

## Description
For debugging only - manually delete an IKE (Internet Key Exchange) Phase 1 Security Association (SA) entry. The SA is identified by the peer's IP address and its associated cookie, which should be provided in hexadecimal format. This command is typically used for troubleshooting VPN tunnel establishments.

## Arguments
| Argument  | Description                                     |
|-----------|-------------------------------------------------|
| `peer_ip` | **Required.** The IP address of the IKE peer.   |
| `cookie`  | **Required.** The IKE SA cookie in hexadecimal format (e.g., `0xabcdef1234567890`). |

## Example usage
```
example_com:velocli> debug --ike_delete_p1_sa 172.16.10.5 0x1a2b3c4d5e6f7890
```
This command attempts to delete the IKE Phase 1 SA associated with peer IP `172.16.10.5` and IKE cookie `0x1a2b3c4d5e6f7890`.

## Field descriptions
| Column | Description |
|---|---|
| N/A    | This command performs an action (deleting an IKE P1 SA) and does not produce a tabular output. Success or failure messages related to the deletion attempt may be displayed on the console. |