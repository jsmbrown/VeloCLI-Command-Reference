#	--app_ip_port_cache_flush

##	Description
Clears the slow learning cache on the VeloCloud Edge. The slow learning cache is utilized by the Edge to store information related to application IP addresses and port numbers, which assists in the application identification process. Flushing this cache can be a useful troubleshooting step for issues concerning application misidentification or stale flow data that might affect Quality of Experience (QoE) policy enforcement.

##  Arguments
This command does not take any arguments.

##  Example usage
```
example_com:velocli> debug --app_ip_port_cache_flush
{
  "Success": "Cleared the slow learning cache"
}

example_com:velocli>
```

##  Field Descriptions
The output is a JSON object confirming the action.

| Field   | Description                                                                      |
|---------|----------------------------------------------------------------------------------|
| Success | A confirmation message indicating that the slow learning cache has been successfully cleared. |