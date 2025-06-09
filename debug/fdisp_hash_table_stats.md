#	--fdisp_hash_table_stats [core-id|all]

##	Description
Show flow dispatcher hash table statistics. The flow dispatcher is responsible for efficiently processing and directing network flows through the VeloCloud Edge. These statistics provide insights into the performance and load of the hash tables used by the flow dispatcher.

##	Arguments (optional)
| Argument | Description |
|---|---|
| `core-id` | Specifies a particular CPU core ID for which to display flow dispatcher hash table statistics. This is useful on multi-core Edges to inspect per-core performance. |
| `all` | Displays flow dispatcher hash table statistics for all CPU cores. |
| *none* | If no argument is provided (as shown in the example), statistics for all relevant cores (or a default/primary core) are displayed. The output will be a JSON array, with each object in the array representing the statistics for one core. |

##	Example usage
```
example_com:velocli> debug --fdisp_hash_table_stats
[
  {
    "avg_bkt_elts": 0.0012367491166077739,
    "avg_bkt_overflow_elts": 0.0,
    "avg_non_uniq_sg_collisions": 0.0,
    "avg_overflowed_bkt_overflow_elts": 0.0
  }
]
```

##	Field descriptions
The output is a JSON array. Each object in the array contains statistics for a specific core's flow dispatcher hash table.
| Field | Description |
|---|---|
| `avg_bkt_elts` | Average number of elements per bucket in the hash table. A lower number generally indicates better hash distribution and fewer collisions. |
| `avg_bkt_overflow_elts` | Average number of elements that are part of an overflow chain, calculated across all buckets. Ideally, this should be close to 0. |
| `avg_non_uniq_sg_collisions` | Average number of collisions encountered for non-unique Source/Group (SG) pairs. This metric can indicate the efficiency of hashing for flows, potentially related to multicast or similarly grouped traffic. |
| `avg_overflowed_bkt_overflow_elts` | Average number of overflow elements specifically within buckets that have already overflowed. This provides insight into the depth of overflow chains for contended buckets. |