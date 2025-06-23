#	--debug_path_uptime

##	Description
This command dumps the internal hash table that tracks the uptime and status of various dataplane paths (tunnels) established by the VeloCloud Edge.

##  Arguments
This command takes no arguments.

##  Example usage
```
example_com:velocli> debug --debug_path_uptime
[
  {
    "dst_ip": "20.118.207.159",
    "link_logical_id": "00000001-3913-4132-bca0-dd18bdf45da5",
    "path_state": 9,
    "standby": false,
    "start_time_ms": 1626018054,
    "tunnel_up": true,
    "tunnel_up_duration_ms": 0,
    "tunnel_up_time_ms": 1626018054
  }
]
```

##  Field descriptions
The output is a JSON array, where each object represents a monitored path and contains the following fields:

| Field             | Description                                                                                                |
|-------------------|------------------------------------------------------------------------------------------------------------|
| `dst_ip`          | The destination IP address of the remote peer (e.g., another VeloCloud Edge, Gateway, or NVS/NSD endpoint) for this path. |
| `link_logical_id` | The unique logical identifier of the local WAN link on the Edge over which this path is established.       |
| `path_state`      | A numerical value representing the current operational state of the path. For example, '9' might indicate an active and stable state. |
| `standby`         | A boolean value indicating whether this path is currently designated as a standby path (`true`) or an active path (`false`). |