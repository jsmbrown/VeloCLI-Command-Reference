#	--rx_bw_cap_kbps &lt;INTERFACE&gt; &lt;KBPS&gt;

##	Description
Configures an explicit cap on the downstream (receive) bandwidth for a specified WAN interface on the VeloCloud Edge. This command allows administrators to manually limit the ingress traffic rate on a particular link. This can be useful for traffic shaping, ensuring fair usage across multiple links, or adhering to specific bandwidth limitations imposed by an internet service provider.

##  Arguments
| Argument    | Description                                                                 |
|-------------|-----------------------------------------------------------------------------|
| `INTERFACE` | The logical name of the WAN interface on the Edge to which the bandwidth cap will be applied (e.g., GE1, GE2, SFP1, USB1). |
| `KBPS`      | The desired maximum downstream bandwidth cap, specified in kilobits per second (Kbps). This value dictates the upper limit for received traffic on the interface. |

##  Example Usage
To cap the downstream bandwidth on the interface `GE1` to 50 Mbps (which is 50,000 Kbps):
```
example_com:velocli> debug --rx_bw_cap_kbps GE1 50000
```
This command typically applies the configuration change directly. Successful execution may not produce any specific output message. To verify the change, one might need to observe traffic statistics or link performance through the VeloCloud Orchestrator or other Edge CLI commands.

The usage message shown in the problem description (`usage: debug.py [-h] ...`) appears when the command is entered without the required `INTERFACE` and `KBPS` arguments.

##  Field Descriptions
This command is used to configure a setting on the VeloCloud Edge and does not produce a tabular output of data. Therefore, a "Field Descriptions" section detailing output columns is not applicable.