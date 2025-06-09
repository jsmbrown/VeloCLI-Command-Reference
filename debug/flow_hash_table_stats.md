#	--flow_hash_table_stats

##	Description
Displays statistics related to the flow hash table. The flow hash table is a critical data structure used by the VeloCloud Edge to efficiently store and retrieve information about active network flows. This allows for rapid lookup and processing of packets belonging to existing sessions.

##  Arguments
This command takes no arguments.

##  Example usage
```
example_com:velocli> debug --flow_hash_table_stats
{
  "flow_table_stats": {
    "avg_bkt_elts": 0.025535714285714287,
    "avg_bkt_overflow_elts": 0.0,
    "avg_non_uniq_sg_collisions": 0.0,
    "avg_overflowed_bkt_overflow_elts": 0.0
  }
}
```

##  Field descriptions
| Field                                  | Description                                                                                                                               |
|----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| `flow_table_stats`                     | Parent object containing all flow hash table statistics.                                                                                    |
| `avg_bkt_elts`                         | Average number of elements (flows) per hash bucket. A lower number generally indicates better hash distribution and fewer collisions.         |
| `avg_bkt_overflow_elts`                | Average number of elements in overflow chains per bucket. This indicates how many flows could not fit into their primary hash bucket.         |
| `avg_non_uniq_sg_collisions`           | Average number of collisions for non-unique source/group (SG) pairs. This can occur if multiple flows hash to the same bucket and have similar SG characteristics. |
| `avg_overflowed_bkt_overflow_elts`     | Average number of overflow elements specifically for buckets that have experienced an overflow. This provides insight into the depth of overflow chains. |