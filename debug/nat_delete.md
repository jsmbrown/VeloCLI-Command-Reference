#	--nat_delete &lt;seg_id&gt; &lt;src_ip&gt; &lt;src_port&gt; &lt;dst_ip&gt; &lt;dst_port&gt; &lt;proto&gt; &lt;nat_type&gt;

##	Description
This command deletes a specific Network Address Translation (NAT) entry from the VeloCloud Edge's NAT table. The entry is identified by its original five-tuple (source IP, source port, destination IP, destination port, protocol) and the NAT type, all within a specified segment.

##  Arguments (mandatory)
| Argument | Description |
|---|---|
| &lt;seg_id&gt; | The segment ID associated with the NAT entry. |
| &lt;src_ip&gt; | The original source IP address of the flow. |
| &lt;src_port&gt; | The original source port of the flow. |
| &lt;dst_ip&gt; | The original destination IP address of the flow. |
| &lt;dst_port&gt; | The original destination port of the flow. |
| &lt;proto&gt; | The protocol of the flow (e.g., `tcp`, `udp`, `icmp`). |
| &lt;nat_type&gt; | The type of NAT applied to the flow (e.g., `sourceNat`, `destinationNat`). The specific values for `nat_type` may vary based on the NAT configuration. |

##  Example usage
```
example_com:velocli> debug --nat_delete 1 192.168.10.50 54321 8.8.8.8 53 udp sourceNat
```
*(Note: Successful execution of this command may not produce output, or it might return a simple confirmation message. The exact output can vary.)*

##  Field descriptions
This command is used to delete an entry and typically does not produce tabular output with fields to describe. If the command is successful, the specified NAT entry will be removed. If an error occurs (e.g., entry not found), an error message may be displayed.