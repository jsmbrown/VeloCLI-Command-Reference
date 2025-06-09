#	--nat_port_hash_table_stats

##	Description
Displays statistics related to the Network Address Translation (NAT) port hash table. This table is used by the VeloCloud Edge to manage and track NAT sessions, specifically the mapping of internal source IP addresses and ports to external IP addresses and ports. The statistics provide insights into the efficiency and utilization of this hash table.

##  Arguments
This command takes no arguments.

##  Example usage
```
example_com:velocli> debug --nat_port_hash_table_stats
{
  "nat_port_table_stats": {
    "avg_bkt_elts": 0.0017857142857142857,
    "avg_bkt_overflow_elts": 0.0,
    "avg_non_uniq_sg_collisions": 0.0,
    "avg_overflowed_bkt_overflow_elts": 0.0
  }
}
```

##  Field descriptions
| Field                                  | Description                                                                                                |
|----------------------------------------|------------------------------------------------------------------------------------------------------------|
| `nat_port_table_stats`                 | Parent key for all NAT port hash table statistics.                                                         |
| `avg_bkt_elts`                         | Average number of elements (NAT entries) per hash bucket. A lower number generally indicates better distribution. |
| `avg_bkt_overflow_elts`                | Average number of elements that have overflowed from their original hash bucket into an overflow structure.    |
| `avg_non_uniq_sg_collisions`           | Average number of collisions encountered for non-unique source group (IP address and port) mappings.         |
| `avg_overflowed_bkt_overflow_elts`     | Average number of overflow elements specifically within buckets that have experienced an overflow.             |