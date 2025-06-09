# --nat_hash_table_stats

## Description
Displays statistics related to the Network Address Translation (NAT) hash table. This information can be useful for diagnosing NAT performance and capacity issues on the VeloCloud Edge. The statistics provide insights into the efficiency of the hash table, such as collision rates and bucket utilization.

## Arguments (optional)
This command takes no arguments.

## Example usage
```
example_com:velocli> debug --nat_hash_table_stats
{
  "nat_modified_table_stats": {
    "avg_bkt_elts": 0.013035714285714286,
    "avg_bkt_overflow_elts": 0.0,
    "avg_non_uniq_sg_collisions": 0.0,
    "avg_overflowed_bkt_overflow_elts": 0.0,
    "bkt_count": 134217728,
    "bkt_overflow_count": 0,
    "elt_count": 1749600,
    "elt_overflow_count": 0,
    "max_bkt_elts": 3,
    "max_bkt_overflow_elts": 0,
    "max_non_uniq_sg_collisions": 0,
    "max_overflowed_bkt_overflow_elts": 0,
    "non_uniq_sg_collision_count": 0,
    "non_uniq_sg_count": 0
  }
}
```

## Field descriptions
| Field                                  | Description                                                                                                |
| :------------------------------------- | :--------------------------------------------------------------------------------------------------------- |
| `nat_modified_table_stats`             | Parent object containing all NAT hash table statistics.                                                    |
| `avg_bkt_elts`                         | Average number of elements (NAT entries) per hash bucket.                                                  |
| `avg_bkt_overflow_elts`                | Average number of elements in overflow chains per bucket.                                                  |
| `avg_non_uniq_sg_collisions`           | Average number of collisions for non-unique source groups (SG). This may relate to specific NAT mapping types. |
| `avg_overflowed_bkt_overflow_elts`     | Average number of overflow elements specifically within buckets that have experienced an overflow.         |
| `bkt_count`                            | Total number of buckets in the NAT hash table.                                                             |
| `bkt_overflow_count`                   | Total number of buckets that have overflowed (i.e., contain more elements than their primary capacity).    |
| `elt_count`                            | Total number of elements (active NAT entries) in the hash table.                                           |
| `elt_overflow_count`                   | Total number of elements that are stored in overflow chains.                                               |
| `max_bkt_elts`                         | Maximum number of elements found in any single hash bucket.                                                |
| `max_bkt_overflow_elts`                | Maximum number of overflow elements associated with any single bucket.                                     |
| `max_non_uniq_sg_collisions`           | Maximum number of collisions observed for non-unique source groups.                                        |
| `max_overflowed_bkt_overflow_elts`     | Maximum number of overflow elements found in any single bucket that has overflowed.                        |
| `non_uniq_sg_collision_count`          | Total count of collisions involving non-unique source groups.                                              |
| `non_uniq_sg_count`                    | Total count of non-unique source groups.                                                                   |