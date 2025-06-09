#	--nat_db_flush [v4 | v6 | all]

##	Description
Flushes the Network Address Translation (NAT) database entries on the VeloCloud Edge. This operation clears active NAT sessions, which can be useful for troubleshooting connectivity problems or ensuring that new NAT policies are applied immediately without waiting for existing sessions to time out. This command affects the dataplane component of the VeloCloud Edge.

##  Arguments (optional)
| Argument | Description |
|---|---|
| `v4` | Specifies that only IPv4 NAT entries should be flushed from the database. |
| `v6` | Specifies that only IPv6 NAT entries should be flushed from the database. |
| `all` | Specifies that both IPv4 and IPv6 NAT entries should be flushed. This is the default action if no argument is provided. |

##  Example usage
Flush all NAT entries (default behavior):
```
example_com:velocli> debug --nat_db_flush
{
  "ALERT": "NAT database cleaned up"
}
```

Flush only IPv4 NAT entries:
```
example_com:velocli> debug --nat_db_flush v4
{
  "ALERT": "NAT database cleaned up"
}
```

Flush only IPv6 NAT entries:
```
example_com:velocli> debug --nat_db_flush v6
{
  "ALERT": "NAT database cleaned up"
}
```

##  Field descriptions
The command returns a JSON object with the following field:

| Field   | Description                                                                 |
|---------|-----------------------------------------------------------------------------|
| `ALERT` | A confirmation message indicating that the NAT database has been cleaned up. |