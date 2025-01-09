#	--dec

##	Description
Dump the dynamic error correction status and QoE scoring detail of all overlay paths.  Outputs include the latency, jitter, and packet loss values observed in both the tx and rx direction for each overlay path/tunnel established on the edge.  Output also includes a red/yellow/green QoE score value based on the thresholds outlined in [this kb article](https://knowledge.broadcom.com/external/article/330715/vmware-sdwan-edge-link-selection-behavio.html).

##  Arguments
None

##  Example usage
```
example_com:velocli> debug --dec
Element   |            Dest  |           Dest  |  Subpath  |  Mode  |  LATENCY  LATENCY  LATENCY  LATENCY  |  JITTER  JITTER  JITTER  JITTER  |  LOSS   LOSS   LOSS   LOSS
Name      |            Name  |             Ip  |   COS ID  |  Mode  |       ms    VOICE    VIDEO    TRANS  |      ms   VOICE   VIDEO   TRANS  |   PCT  VOICE  VIDEO  TRANS
GE1       |             N/A  |            N/A  |      N/A  |    TX  |        0    green    green    green  |       0   green   green   green  |   0.0  green  green  green
GE1       |             N/A  |            N/A  |      N/A  |    RX  |        0    green    green    green  |       0   green   green   green  |   0.0  green  green  green
GE1       |       AzurevWAN  |  20.46.246.159  |       -1  |    TX  |        0    green    green    green  |       0   green   green   green  |   0.0  green  green  green
GE1       |       AzurevWAN  |  20.46.246.159  |       -1  |    RX  |        0    green    green    green  |       0   green   green   green  |   0.0  green  green  green
GE1       |  vNET Peer Test  |   20.29.48.111  |       -1  |    TX  |        0    green    green    green  |       1   green   green   green  |   0.0  green  green  green
GE1       |  vNET Peer Test  |   20.29.48.111  |       -1  |    RX  |        0    green    green    green  |       0   green   green   green  |   0.0  green  green  green
GE1       |      vcg44-dfw1  |  216.221.31.44  |       -1  |    TX  |        6    green    green    green  |       0   green   green   green  |   0.0  green  green  green
GE1       |      vcg44-dfw1  |  216.221.31.44  |       -1  |    RX  |        5    green    green    green  |       0   green   green   green  |   0.0  green  green  green
GE1       |      vcg88-ord1  |  216.221.27.88  |       -1  |    TX  |        8    green    green    green  |       0   green   green   green  |   0.0  green  green  green
GE1       |      vcg88-ord1  |  216.221.27.88  |       -1  |    RX  |        5    green    green    green  |       0   green   green   green  |   0.0  green  green  green
* indicates state pending transition
```

##  Field descriptions
| Column | Description |
|---|---|
| Element Name | WAN interface that path is established on |
| Dest Name | Name of the peer edge/gateway that the associated tunnel is built to |
| Dest IP | IP address of the remote edge/gateway tunnel interface |
| Subpath COS ID | Class Of Service value assigned to the sub-path if configured ('-1' if no sub-paths) |
| Mode | Directionality of path values ('TX' for the transmit direction, 'RX' for receive) |
| Latency | Latency measurement in milliseconds with QoE scores for voice, video, and transactional thresholds |
| Jitter | Jitter measurement in milliseconds with QoE scores for voice, video, and transactional thresholds |
| Loss | Percentage of packet loss with QoE scores for voice, video, and transactional thresholds |