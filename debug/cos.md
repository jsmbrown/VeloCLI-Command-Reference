#	--cos

##	Description
The `debug --cos` command is used to display the Classes of Service (CoS) configured for the links on the VeloCloud Edge. This information is crucial for understanding how different types of traffic are prioritized and handled across the SD-WAN fabric, impacting Quality of Experience (QoE).

##  Arguments (optional)
This command does not take any arguments.

##  Example usage
```
example_com:velocli> debug --cos
{
  "Error": "No Links Found"
}

example_com:velocli>
```

##  Field descriptions
The command output will be in JSON format.
If no links are found or configured on the Edge, the output will display an error message as shown in the example:
```json
{
  "Error": "No Links Found"
}
```
If links with Classes of Service are configured, the output would typically detail the CoS queues, their associated DSCP markings, bandwidth allocations, and other relevant parameters for each link. (Note: A positive output example is not provided, but this describes the expected information.)