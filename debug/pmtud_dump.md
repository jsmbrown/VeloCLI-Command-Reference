#	--pmtud_dump [all | peer_name | td_version | interface]

##	Description
Displays the Maximum Transmission Unit (MTU) values detected by the Path Layer Path MTU Discovery (PLPMTUD) module. This module is responsible for determining the optimal MTU for paths to avoid IP fragmentation and ensure efficient data transmission.

##  Arguments (optional)
One of the following arguments can be specified to filter the output:

| Argument     | Description                                                                        |
|--------------|------------------------------------------------------------------------------------|
| `all`        | (Default if no argument is specified) Show PMTUD information for all detected paths. |
| `peer_name`  | Show PMTUD information for paths associated with the specified peer name.          |
| `td_version` | Show PMTUD information filtered by a specific tunnel discovery (TD) version.       |
| `interface`  | Show PMTUD information for paths utilizing the specified network interface.        |

##  Example Usage
```
example_com:velocli> debug --pmtud_dump
{
  "Error": "No Paths Found"
}

example_com:velocli>
```
**Note:** The example above shows the output when no paths with PMTUD information are found. A successful execution would list details of paths and their discovered MTUs.

##  Field Descriptions
The output is in JSON format. The fields displayed will vary based on whether paths are found and the specific arguments used.

| Field   | Description                                                                 |
|---------|-----------------------------------------------------------------------------|
| `Error` | (Conditional) Displays an error message, such as "No Paths Found", if applicable. |
| *(Other fields)* | *When paths are found, the output will typically include details such as peer identifiers, interface names, path MTU values, and timestamps. Specific field names would be present in a successful output.* |