#	--ike_spd [all | peer_ip]

##	Description
Dumps the current IKE (Internet Key Exchange) Security Policy Database (SPD) on the VeloCloud Edge or Gateway. The SPD is a critical component of IPSec, defining policies that determine which network traffic is to be protected by encrypted tunnels (paths) and the security parameters for that protection. This is particularly useful for troubleshooting IPSec tunnel formation and traffic processing.

##  Arguments (optional)
| Argument | Description |
|---|---|
| `all` | (Default if no argument is specified) Displays all entries in the IKE Security Policy Database. |
| `peer_ip` | Displays IKE Security Policy Database entries specific to the given peer IP address. This helps in isolating policies related to a particular IPSec peer. |

##  Example usage
```
example_com:velocli> debug --ike_spd
Security Policy
===============================================================================================================================================================
Version   Cookie       Mode  SecuProto  P1Auth  P1Encr  DHGroup  DPDTimeout  P1SALife  P2Auth       P2Encr  PFS  P2SALife                 TunnelEndpoints
v2          0xd8  Transport   ESP_AUTH     Any     Any       20           0     86400   SHA_1  AES_256_GCM   20     28800   172.30.0.6 <==> 216.221.31.44
v2          0xd7  Transport   ESP_AUTH     Any     Any       20           0     86400   SHA_1  AES_256_GCM   20     28800   172.30.0.6 <==> 216.221.27.88
v2           0x3     Tunnel   ESP_NULL     Any     Any       14          20     86400   SHA_1          Any   14     28800  172.30.0.6 <<=>> 170.85.14.130
```

##  Field descriptions
| Column | Description |
|---|---|
| Version | IKE protocol version used for the policy (e.g., `v2` for IKEv2). |
| Cookie | Unique identifier (initiator and responder cookies) for the IKE Security Association (SA). |
| Mode | IKE operational mode: `Transport` mode secures end-to-end communication between two hosts. `Tunnel` mode (more common for VPNs) secures communication between networks or gateways by encapsulating the original IP packet. |
| SecuProto | Security Protocol used, typically ESP (Encapsulating Security Payload). `ESP_AUTH` indicates ESP with authentication. `ESP_NULL` indicates ESP is used but without encryption (payload is not encrypted, though it might still be authenticated), often for specific use cases or when inner encryption exists. |
| P1Auth | Phase 1 Authentication algorithm (e.g., `Any`, `SHA_1`, `SHA256`). This algorithm is used to authenticate the peers during the IKE SA establishment. `Any` may indicate a proposal or willingness to accept multiple types. |
| P1Encr | Phase 1 Encryption algorithm (e.g., `Any`, `AES_128`, `AES_256_GCM`). This algorithm protects the Phase 1 negotiation itself. |
| DHGroup | Diffie-Hellman (DH) group number used for key exchange in Phase 1. This determines the strength of the generated keys. |
| DPDTimeout | Dead Peer Detection timeout in seconds. DPD messages are exchanged to detect if an IKE peer is no longer responsive. A value of `0` might indicate DPD is disabled or using a default system setting. |
| P1SALife | Phase 1 Security Association lifetime in seconds. The IKE SA (Phase 1 SA) will need to be re-negotiated before this timer expires. |
| P2Auth | Phase 2 Authentication algorithm (e.g., `SHA_1`, `SHA256`). This algorithm ensures the integrity of the data traffic protected by the IPSec SA (Child SA). |
| P2Encr | Phase 2 Encryption algorithm (e.g., `AES_256_GCM`, `Any`). This algorithm encrypts the actual user data traffic. `Any` may indicate a proposal or that the specific algorithm is negotiated. |
| PFS | Perfect Forward Secrecy. Specifies the Diffie-Hellman group number for Phase 2 re-keying. If a DH group is specified (e.g., `14`, `20`), PFS is enabled for the Child SA, meaning new session keys are derived independently of previous keys. |
| P2SALife | Phase 2 Security Association (Child SA) lifetime in seconds. The IPSec SA, which protects data traffic, will need to be re-negotiated before this timer expires. |
| TunnelEndpoints | The local and remote IP addresses of the IKE/IPSec tunnel. The symbols `<==>` or `<<=>>` may indicate the directionality of the policy (e.g., inbound, outbound, bidirectional) or how the policy was matched. |