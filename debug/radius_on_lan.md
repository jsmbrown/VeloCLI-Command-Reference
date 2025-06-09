#	--radius_on_lan

##	Description
This command displays debugging information related to RADIUS authentication for clients connected to the LAN bridge interfaces of the VeloCloud Edge. It shows MAC bypass rules and currently known authenticated clients. This is useful for troubleshooting 802.1X or MAC-based authentication issues on the LAN side.

##  Arguments (optional)
| Argument | Description |
|---|---|
| none | This command does not accept any arguments. |

##  Example usage
```
example_com:velocli> debug --radius_on_lan
====================== MAC Bypass Rules ====================
iface   MAC  Hits
====================== Known Clients ====================
iface   MAC  Age(ms)  Last Check(ms)  Flags  Hits

example_com:velocli>
```

##  Field descriptions
The output is divided into two sections:

**MAC Bypass Rules:**
This section lists the configured MAC addresses that are allowed to bypass RADIUS authentication.

| Column | Description |
|---|---|
| `iface` | The LAN interface on which the MAC bypass rule is applied. |
| `MAC`   | The MAC address that is configured to bypass RADIUS authentication. |
| `Hits`  | The number of times this bypass rule has been matched by a connecting client. |

**Known Clients:**
This section lists clients that have been seen or authenticated via RADIUS on the LAN interfaces.

| Column          | Description |
|-----------------|-------------|
| `iface`         | The LAN interface to which the client is connected. |
| `MAC`           | The MAC address of the client. |
| `Age(ms)`       | The duration, in milliseconds, since the client entry was created or last refreshed. |
| `Last Check(ms)`| The time, in milliseconds, since the client's authentication status was last checked. |
| `Flags`         | Flags indicating the status or attributes of the client (e.g., authentication state). Specific flag meanings would require further VeloCloud internal documentation. |
| `Hits`          | The number of packets or authentication attempts associated with this client. |