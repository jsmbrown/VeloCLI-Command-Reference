#	--ike_childsa `[all | v4 | v6 [all | peer_ip [all | ikeSaSpi [count]]]]`

##	Description
This command displays the current IKE (Internet Key Exchange) Child Security Associations (SAs) established by the VeloCloud Edge. Child SAs are created under an IKE SA and define the security parameters for specific IPsec traffic flows, typically for user data. This command is useful for troubleshooting IPsec tunnel connectivity, particularly for Non-VeloCloud Site (NVS) or Non-SD-WAN Destination (NSD) connections.

##  Arguments (optional)
The arguments allow for filtering the displayed Child SAs. They are hierarchical.

| Argument    | Description                                                                 |
|-------------|-----------------------------------------------------------------------------|
| `all`       | (Default if no arguments are provided) Displays all Child SAs.              |
| `v4`        | Displays only IPv4 Child SAs.                                               |
| `v6`        | Displays only IPv6 Child SAs.                                               |
| `peer_ip`   | When used after `v4` or `v6`, filters SAs by the specified peer IP address. |
| `ikeSaSpi`  | When used after `peer_ip`, filters by the parent IKE SA's Security Parameter Index (SPI). |
| `count`     | When used after `ikeSaSpi`, limits the number of displayed SAs to the specified count. |

##  Example usage
```
example_com:velocli> debug --ike_childsa
Child SA = 2
==============================================================================================================================================================================================
Index    Ref  Cookie  SpdId  TunnelId     Flags                 Dir       Spi  PeerPort       Auth  Encr  PFS                                                  Tunnel // Traffic  Pkts  Drops  Interface        Secs
0       0003     0x3   0000         4  0000001d   inbound initiator  d8802f72      4500  sha1-hmac  null   14  172.30.0.6[10001] << 170.85.14.130[4500] // 0.0.0.0/0 < 0.0.0.0/0  3388      0        GE1  3474/28800
1       0003     0x3   0000         4  00000019  outbound initiator  3edb86a5      4500  sha1-hmac  null   14  172.30.0.6[10001] >> 170.85.14.130[4500] // 0.0.0.0/0 > 0.0.0.0/0  5082      0        GE1  3474/28800
```

##  Field descriptions
| Column         | Description                                                                                                |
|----------------|------------------------------------------------------------------------------------------------------------|
| `Index`        | Internal index of the Child SA.                                                                            |
| `Ref`          | Reference count for the SA.                                                                                |
| `Cookie`       | IKE SA cookie associated with this Child SA.                                                               |
| `SpdId`        | Security Policy Database (SPD) ID.                                                                         |
| `TunnelId`     | Identifier for the tunnel this Child SA belongs to.                                                        |
| `Flags`        | Hexadecimal flags indicating the state and properties of the Child SA.                                     |
| `Dir`          | Direction of the SA (`inbound` or `outbound`) and role (`initiator` or `responder`).                       |
| `Spi`          | Security Parameter Index, a unique identifier for this SA.                                                 |
| `PeerPort`     | UDP port used by the peer for IKE/IPsec communication (typically 500 or 4500 for NAT-T).                   |
| `Auth`         | Authentication algorithm used (e.g., `sha1-hmac`).                                                         |
| `Encr`         | Encryption algorithm used (e.g., `aes-cbc-128`, `null` if no encryption).                                  |
| `PFS`          | Perfect Forward Secrecy group used for key exchange (e.g., `14` for DH group 14).                          |
| `Tunnel // Traffic` | Shows the local and remote IP addresses and ports for the IKE SA (`Tunnel`) and the traffic selectors for the Child SA (`Traffic`). `<<` or `<` indicates inbound, `>>` or `>` indicates outbound. |
| `Pkts`         | Number of packets processed by this Child SA.                                                              |
| `Drops`        | Number of packets dropped by this Child SA.                                                                |
| `Interface`    | The local WAN interface (e.g., `GE1`, `PPPoE1`) used for this IPsec tunnel.                                |
| `Secs`         | Current lifetime of the SA in seconds / configured lifetime of the SA in seconds.                          |