#	--arp_dump

##	Description
Dumps the ARP cache for all active interfaces.

##  Arguments
None

##  Example usage

velouser:velocli> debug --arp_dump
|Interface   |   Address  |C-Tag  |Flags  |              Mac  S-Tag         Source Mac    State  Refcnt  Age (in seconds)
|GE1         |172.30.0.1  |    0  |    0  |12:34:56:78:9a:bc      0  00:0d:3a:a4:78:63    ALIVE       1                 4
|GE2         |172.30.1.1  |    0  |    0  |12:34:56:78:9a:bc      0  00:0d:3a:a4:7e:99  REFRESH       1               178