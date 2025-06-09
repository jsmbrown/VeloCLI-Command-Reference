#	--memory_dump

##	Description
This command dumps a summary of current memory allocations, categorized by module or object type. It provides insights into how memory is being utilized by different components of the VeloCloud Edge software. This is particularly useful for troubleshooting memory leaks or understanding memory consumption patterns.

##  Arguments (optional)
This command does not take any arguments.

##  Example usage
```
example_com:velocli> debug --memory_dump
Object Name                                 Objects In-Use  Bytes In-Use  Pre-Allocated Objects  Pre-Allocated Bytes  Overhead
memb.mod_json_t                                       2067         119KB                      0                    0      32KB
memb.mod_qosmos_t                                    36137          65MB                      0                    0     564KB
memb.mod_quicksec_t                                   5133           2MB                      0                    0      80KB
memb.mod_openssl_t                                    6706         331KB                      0                    0     104KB
memb.mod_unknown_t                                       1           105                      0                    0        16
```

##  Field descriptions
| Column                  | Description                                                                 |
|-------------------------|-----------------------------------------------------------------------------|
| Object Name             | The name of the memory module or object type.                               |
| Objects In-Use          | The number of instances of this object currently allocated and in use.      |
| Bytes In-Use            | The total amount of memory currently consumed by the "Objects In-Use".      |
| Pre-Allocated Objects   | The number of objects that were pre-allocated by the system at startup.     |
| Pre-Allocated Bytes     | The total amount of memory set aside for "Pre-Allocated Objects".           |
| Overhead                | The amount of memory used for managing these allocations (e.g., metadata).  |