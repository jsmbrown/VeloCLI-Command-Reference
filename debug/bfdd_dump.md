#	--bfdd_dump

##	Description
Dumps the running FRR BFD configuration as well as the output of the 'show bfd peers' and 'show bfd peers counters' commands.

##  Arguments
None

##  Example usage
```
example_com:velocli> debug --bfdd_dump
show running-config
===================
Building configuration...

Current configuration:
!
frr version 8.2
frr defaults traditional
hostname vc-edge
log file /var/log/bfdd.log
!
password zebra
!
line vty
 access-class vty
!
bfd
 peer 192.168.10.202 local-address 192.168.10.201 vrf [vc:0:1]
  echo-interval 0
  no shutdown
 !
!
end

sh bfd peers
============
BFD Peers:
	peer 192.168.10.202 local-address 192.168.10.201 vrf [vc:0:1]
		ID: 515638323
		Remote ID: 1
		Status: up
		Uptime: 9 day(s), 2 hour(s), 37 minute(s), 9 second(s)
		Diagnostics: ok
		Remote diagnostics: ok
		Local timers:
			Receive interval: 300ms
			Transmission interval: 300ms
			Echo transmission interval: 0ms
		Remote timers:
			Receive interval: 250ms
			Transmission interval: 250ms
			Echo transmission interval: 0ms


sh bfd peers counters
=====================
BFD Peers:
	peer 192.168.10.202 local-address 192.168.10.201 vrf [vc:0:1]
		Control packet input: 3031626 packets
		Control packet output: 2999690 packets
		Echo packet input: 0 packets
		Echo packet output: 0 packets
		Session up events: 1
		Session down events: 0
		Zebra notifications: 3
```