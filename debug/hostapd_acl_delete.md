#	--hostapd_acl_delete <interface> <mac>

##	Description
This command deletes an Access Control List (ACL) entry for a specific MAC address from the hostapd (Host Access Point Daemon) configuration on the specified wireless interface. This is typically used to remove a previously allowed or denied wireless client.

##  Arguments (mandatory)
| Argument    | Description                                      |
|-------------|--------------------------------------------------|
| `<interface>` | The wireless interface name (e.g., `wlan0`, `ath0`). |
| `<mac>`       | The MAC address to be removed from the ACL.      |

##  Example usage
```
example_com:velocli> debug --hostapd_acl_delete wlan0 00:1A:2B:3C:4D:5E
```
This command would attempt to delete the MAC address `00:1A:2B:3C:4D:5E` from the ACL of the `wlan0` interface.

##  Field descriptions
This command does not produce tabular output. It performs an action (deleting an ACL entry). Success or failure messages may be printed to the console.