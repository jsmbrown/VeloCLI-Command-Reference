#	--port_screen_dump

##	Description
Dump optional Port Scan Screening configuration. This command displays the current status of the Port Scan Screening feature on the VeloCloud Edge. Port Scan Screening is a security mechanism that helps detect potential port scan attacks against the appliance.

##  Arguments
This command takes no arguments.

##  Example usage
```
example_com:velocli> debug --port_screen_dump
{
  "port_scan_screen": "disabled"
}
```

##  Field descriptions
| Field              | Description                                                                                                |
|--------------------|------------------------------------------------------------------------------------------------------------|
| `port_scan_screen` | Indicates the current status of the Port Scan Screening feature. Possible values include:<ul><li>`"disabled"`: Port Scan Screening is currently inactive.</li><li>`"enabled"`: Port Scan Screening is currently active.</li></ul> |