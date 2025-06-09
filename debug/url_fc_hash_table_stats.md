#	--url_fc_hash_table_stats

##	Description
Displays statistics for the EFS (Enhanced Flow Services) URL Flow Control (FC) hash table. These statistics provide insights into the performance and utilization of the hash table, which is likely used for efficient lookup and management of URL-based flow control rules or policies on the VeloCloud Edge.

##  Arguments (optional)
This command does not take any arguments.

##  Example usage
```
example_com:velocli> debug --url_fc_hash_table_stats
{
  "url_fc_map_table_stats": {
    "avg_bkt_elts": 0.0,
    "avg_bkt_overflow_elts": 0.0,
    "avg_non_uniq_sg_collisions": 0.0,
    "avg_overflowed_bkt_overflow_elts": 0.0
  }
}
```

##  Field descriptions
The output is in JSON format.

| Key Path                                 | Description                                                                                                                               |
|------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| `url_fc_map_table_stats`                 | A JSON object containing the statistics for the URL Flow Control map table.                                                               |
| `url_fc_map_table_stats.avg_bkt_elts`    | Average number of elements per hash bucket in the URL Flow Control map table. This indicates the average fill rate of the buckets.          |
| `url_fc_map_table_stats.avg_bkt_overflow_elts` | Average number of elements that overflowed their primary hash bucket and had to be placed in an overflow structure. A higher value might suggest hash collisions or that the table size is insufficient for the current load. |
| `url_fc_map_table_stats.avg_non_uniq_sg_collisions` | Average number of non-unique "sg" collisions. "sg" likely refers to a classification entity (e.g., service group, signature group) used in URL flow control. Collisions occur when different keys hash to the same bucket. |
| `url_fc_map_table_stats.avg_overflowed_bkt_overflow_elts` | Average number of overflow elements specifically within buckets that are already in an overflow state. This metric provides insight into the depth or chaining of overflows. |