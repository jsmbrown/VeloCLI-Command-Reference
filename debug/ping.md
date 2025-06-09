#	--ping &lt;src-ip | src-ifname&gt; &lt;dest-ip | dest-hostname&gt; &lt;seg-id&gt;

##	Description
The `debug --ping` command is a utility used to send ICMP (Internet Control Message Protocol) echo requests to a target host to test network reachability and measure round-trip time. This is a fundamental tool for network troubleshooting on the VeloCloud Edge. It allows specifying the source interface or IP address, the destination IP address or hostname, and the network segment from which the ping originates. This helps in diagnosing connectivity issues across different network paths and segments within the SD-WAN overlay.

##  Arguments (mandatory)
| Argument | Description |
|---|---|
| `&lt;src-ip | src-ifname&gt;` | Specifies the source IP address (e.g., `192.168.1.1`) or the logical interface name (e.g., `GE1`, `GE2`, `SFP1`, `USB1`) on the VeloCloud Edge from which the ICMP ping packets will be sent. |
| `&lt;dest-ip | dest-hostname&gt;` | Specifies the destination IP address (e.g., `8.8.8.8`) or a fully qualified domain name (e.g., `www.google.com`) that the ping requests will be sent to. |
| `&lt;seg-id&gt;` | Specifies the numerical ID of the VeloCloud segment to use for sourcing the ping traffic. Segments are used for network traffic isolation, and specifying the segment ID ensures the ping test is conducted within the correct network context. |

##  Example usage
This example shows pinging the host `google.com` from the interface `GE1` within segment `1`.

```
example_com:velocli> debug --ping GE1 google.com 1
PING google.com (142.250.190.142) from GE1 (10.0.1.5) segment 1: 56(84) bytes of data.
64 bytes from 142.250.190.142 (lhr48s10-in-f14.1e100.net): icmp_seq=1 ttl=115 time=10.2 ms
64 bytes from 142.250.190.142 (lhr48s10-in-f14.1e100.net): icmp_seq=2 ttl=115 time=9.8 ms
64 bytes from 142.250.190.142 (lhr48s10-in-f14.1e100.net): icmp_seq=3 ttl=115 time=10.5 ms

--- google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 9.800/10.166/10.500/0.289 ms
```

If mandatory arguments are omitted, the command will display usage instructions:
```
example_com:velocli> debug --ping
usage: debug.py [-h] [--mode_link] [--timeout TIMEOUT SECONDS]
                [--logfile LOGFILE] [--limit N] [-v]
                [--biz_pol_dump [[all | segment-id] [[all | policy-name]
                ...]]] [--netflow_intervals] [--netflow_collectors]
                [--netflow_filters [<collector_id>]] [--bw_testing_dump]
                [--chat_stats [[sip=] [dip=] [dport=] [app_id=]
                ...]]
                ...
debug.py: error: the following arguments are required: src_ip_or_ifname, dest_ip_or_hostname, seg_id
```

##  Field descriptions
The output of the `debug --ping` command typically includes the following information:

| Field/Line | Description |
|---|---|
| `PING <hostname> (<IP_address>) from <source_interface> (<source_IP>) segment <segment_id>: <data_size>(<total_size>) bytes of data.` | This is the initial line summarizing the ping operation. <br/>&nbsp;&nbsp;&nbsp;&nbsp;`&lt;hostname&gt;`: The target hostname specified in the command. <br/>&nbsp;&nbsp;&nbsp;&nbsp;`&lt;IP_address&gt;`: The resolved IP address of the target hostname. <br/>&nbsp;&nbsp;&nbsp;&nbsp;`&lt;source_interface&gt;`: The source interface used for the ping, if specified. <br/>&nbsp;&nbsp;&nbsp;&nbsp;`&lt;source_IP&gt;`: The IP address of the source interface/IP used for the ping. <br/>&nbsp;&nbsp;&nbsp;&nbsp;`&lt;segment_id&gt;`: The segment ID from which the ping is sourced. <br/>&nbsp;&nbsp;&nbsp;&nbsp;`&lt;data_size&gt;`: The size of the ICMP payload in bytes. <br/>&nbsp;&nbsp;&nbsp;&nbsp;`&lt;total_size&gt;`: The total size of the ICMP packet including headers. |
| `X bytes from <IP_address> (<resolved_hostname>): icmp_seq=N ttl=T time=R ms` | This line appears for each ICMP echo reply received. <br/>&nbsp;&nbsp;&nbsp;&nbsp;`X bytes from &lt;IP_address&gt;`: Indicates a reply was received from the specified IP address. <br/>&nbsp;&nbsp;&nbsp;&nbsp;`&lt;resolved_hostname&gt;`: Reverse DNS lookup of the replying IP address, if available. <br/>&nbsp;&nbsp;&nbsp;&nbsp;`icmp_seq=N`: The sequence number of the ICMP packet. This increments for each packet sent. <br/>&nbsp;&nbsp;&nbsp;&nbsp;`ttl=T`: The Time-To-Live value from the IP header of the reply. This indicates how many more router hops the packet could have traversed. <br/>&nbsp;&nbsp;&nbsp;&nbsp;`time=R ms`: The round-trip time (RTT) for this specific packet, measured in milliseconds. This is the time taken for the packet to go to the destination and return. |
| `--- <hostname> ping statistics ---` | Header for the summary statistics section. |
| `X packets transmitted, Y received, Z% packet loss, time Tms` | This line summarizes the results of the entire ping session. <br/>&nbsp;&nbsp;&nbsp;&nbsp;`packets transmitted`: Total number of ICMP echo request packets sent. <br/>&nbsp;&nbsp;&nbsp;&nbsp;`received`: Total number of ICMP echo reply packets received. <br/>&nbsp;&nbsp;&nbsp;&nbsp;`packet loss`: Percentage of packets that were sent but for which no reply was received. <br/>&nbsp;&nbsp;&nbsp;&nbsp;`time`: Total duration of the ping session in milliseconds. |
| `rtt min/avg/max/mdev = A/B/C/D ms` | This line provides statistics on the round-trip times for all received replies. <br/>&nbsp;&nbsp;&nbsp;&nbsp;`min`: Minimum round-trip time observed. <br/>&nbsp;&nbsp;&nbsp;&nbsp;`avg`: Average round-trip time. <br/>&nbsp;&nbsp;&nbsp;&nbsp;`max`: Maximum round-trip time observed. <br/>&nbsp;&nbsp;&nbsp;&nbsp;`mdev`: Mean deviation of the round-trip times, indicating the variability in RTT. |