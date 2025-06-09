#	--ike [all | v4 | v6]

##	Description
Dumps the current Internet Key Exchange (IKE) descriptors. This command is used to inspect the state and configuration parameters of IKE sessions, which are fundamental for establishing IPsec tunnels. In the VeloCloud SD-WAN solution, IKE is primarily used for creating secure tunnels to Non-VeloCloud Sites (NVS), also known as Non-SD-WAN Destinations (NSD), and to VeloCloud Gateways for specific services.

##  Arguments (optional)
| Argument | Description |
|---|---|
| `all` | (Default if no argument is specified) Dumps all IKE descriptors for both IPv4 and IPv6. |
| `v4` | Dumps only IKE descriptors related to IPv4. |
| `v6` | Dumps only IKE descriptors related to IPv6. |

##  Example usage
```json
example_com:velocli> debug --ike
{
  "descriptors": [
    {
      "P1AuthAlgo": "Any",
      "P1DHgroup": 14,
      "P1EncrAlgo": "Any"
      // Note: A complete output would typically include more fields.
    }
  ]
}
```

##  Field descriptions
The output is a JSON object containing a top-level key `descriptors`, which is an array of IKE descriptor objects. Each object in this array represents an active or configured IKE session and provides details about its parameters.

Based on the provided example, the following fields are shown for each descriptor:

| Key | Description |
|---|---|
| `P1AuthAlgo` | The authentication algorithm negotiated or configured for IKE Phase 1. "Any" suggests flexibility in negotiation or a placeholder if the Security Association (SA) is not fully established. Common values include SHA1, SHA256, etc. |
| `P1DHgroup` | The Diffie-Hellman (DH) group number used for key exchange during IKE Phase 1. Group 14 corresponds to a 2048-bit MODP (Modular Exponentiation) group, providing strong keying material. |
| `P1EncrAlgo` | The encryption algorithm negotiated or configured for IKE Phase 1. "Any" suggests flexibility in negotiation. Common values include AES-128, AES-256, 3DES. |

**Note:** A complete output for `debug --ike` would typically include a more comprehensive set of fields for each IKE descriptor, such as:
*   **IKE Phase 1 (IKE SA) details:** Lifetime (e.g., `P1Lifetime`), local/remote identifiers (e.g., `local_id`, `remote_id`), local/remote IP addresses (e.g., `local_ip`, `remote_ip`), IKE version (e.g., `ike_version` which could be 1 for IKEv1 or 2 for IKEv2), NAT Traversal status (e.g., `nat_traversal`), Dead Peer Detection (DPD) status.
*   **IKE Phase 2 (IPsec SA/Child SA) details:** Encryption and authentication algorithms (e.g., `P2EncrAlgo`, `P2AuthAlgo`), Perfect Forward Secrecy (PFS) DH group (e.g., `P2PFSgroup`), lifetime (e.g., `P2Lifetime`), local/remote traffic selectors (subnets, e.g., `local_ts`, `remote_ts`).
*   **Peer Information:** Name or identifier of the remote peer (e.g., `peer_name`, often corresponding to a configured Non-VeloCloud Site or Gateway).
*   **Status:** Current operational status of the IKE SA (e.g., `status` which could be UP, DOWN, NEGOTIATING).
*   **Associated Interfaces:** The VeloCloud Edge interface (e.g., `interface_name`) associated with the tunnel.

This additional information is crucial for diagnosing IPsec tunnel connectivity and negotiation issues.