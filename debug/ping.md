#	--ping &lt;src-ip | src-ifname&gt; &lt;dest-ip | dest-hostname&gt; &lt;seg-id&gt;

##	Description
The `debug --ping` command is a utility used to send ICMP (Internet Control Message Protocol) echo requests to a target host to test network reachability and measure round-trip time.  It allows specifying the source interface or IP address, the destination IP address or hostname, and the network segment from which the ping originates. This helps in diagnosing connectivity issues across different network paths and segments within the SD-WAN overlay.

##  Arguments (mandatory)
| Argument | Description |
|---|---|
| `&lt;src-ip | src-ifname&gt;` | Specifies the source IP address (e.g., `192.168.1.1`) or the logical interface name (e.g., `GE1`, `GE2`, `SFP1`, `USB1`) on the VeloCloud Edge from which the ICMP ping packets will be sent. |
| `&lt;dest-ip | dest-hostname&gt;` | Specifies the destination IP address (e.g., `8.8.8.8`) or a fully qualified domain name (e.g., `www.google.com`) that the ping requests will be sent to. |
| `&lt;seg-id&gt;` | Specifies the numerical ID of the VeloCloud segment to use for sourcing the ping traffic. Segments are used for network traffic isolation, and specifying the segment ID ensures the ping test is conducted within the correct network context. |

##  Example usage
This example shows pinging the IP address `10.10.10.1` from `1.2.3.4` within segment `1`.

```
example_com:velocli> debug --ping 1.2.3.4 10.10.10.1 1
[
  {
    "cum_rtt": 221,
    "dst": "10.10.10.1",
    "max_rtt": 33,
    "min_rtt": 28,
    "reachable": "yes",
    "reply_count": 7,
    "request_count": 7,
    "src": "1.2.3.4"
  }
]
```

##  Field descriptions
The output of the `debug --ping` command typically includes the following information:

| Field/Line | Description |
|---|---|
| `cum_rtt` | Cumulative round trip time for all requests in milliseconds |
| `dst` | Destination IP or hostname against which the test was run |
| `max_rtt` | Highest recorded round trip time in milliseconds. |
| `min_rtt` | Lowest recorded round trip time in milliseconds. |
| `reachable` | `yes` if any responses were received from the target IP/hostname |
| `reply_count` | Number of ICMP echo replies received from the target IP/hostname. |
| `request_count` | Number of ICMP echo requests sent to the target IP/hostname. |
| `src` | IP or hostname that pings are sourced from |