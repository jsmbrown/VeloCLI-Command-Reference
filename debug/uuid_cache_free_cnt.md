#	--uuid_cache_free_cnt

##	Description
This command displays the number of available entries in the UUID (Universally Unique Identifier) cache on the VeloCloud Edge. The UUID cache is used to store identifiers for various entities within the SD-WAN fabric, such as other Edges, Gateways, or network services. Monitoring the free count can help in understanding the capacity and utilization of this cache.

##  Arguments (optional)
This command does not take any arguments.

##  Example usage
```
example_com:velocli> debug --uuid_cache_free_cnt
{
  "UUID Cache free count": 65531
}

example_com:velocli>
```

##  Field descriptions
| Field                   | Description                                                                 |
|-------------------------|-----------------------------------------------------------------------------|
| UUID Cache free count   | The number of unused or available entries currently in the Edge's UUID cache. |