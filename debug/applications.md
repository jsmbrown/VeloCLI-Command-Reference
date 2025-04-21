#	--applications

##	Description
Dumps a list of all applications in the current app-map along with basic high level attributes.

##  Arguments
None

##  Example usage
```
example_com:velocli> debug --applications
NAME                                                                                       DISPLAY  APP_ID  CLASS_ID  IP ROUTABLE  PORT ROUTABLE
APP_UNCLASSIFIED                                                                      unclassified       0         0        False          False
APP_BASE                                                                                      base       3        13        False          False
APP_UNKNOWN                                                                                unknown       4         0        False          False
APP_MALFORMED                                                                            malformed       5        13        False          False
APP_INCOMPLETE                                                                          incomplete       6        13        False          False
APP_8021Q                                                                                    8021q       7        13        False          False
APP_AIM                                                                                        aim       8        10        False          False
APP_AMQP                                                                                      amqp       9        13        False          False
APP_APOLLO                                                                                  apollo      10        13        False          False
APP_ARP                                                                                        arp      11        13        False          False
APP_ATALK                                                                                    atalk      12        13        False          False
APP_BGP                                                                                        bgp      13        13        False           True
APP_BITTORRENT                                                                          bittorrent      15        14        False          False

```

##  Field descriptions
| Column | Description |
|---|---|
| NAME | Name of the application as configured in the app map. |
| DISPLAY | Name of the application as displayed in flow dumps, app chat stats, etc. |
| APP_ID | Numerical id of the application as configured in the app map |
| CLASS_ID | Numerical id of the application category as configured in the app map |
| IP ROUTABLE | Indicates whether the app definition maps to known IP address(es) with the option to also specify known TCP/UDP ports |
| PORT ROUTABLE | Indicates whether the app definition maps to TCP/UDP ports only |
