#	--profile_dump

##	Description
Dumps the configuration profiles associated with the enterprise. Profiles in VeloCloud SD-WAN define common configurations that can be applied to multiple Edges, simplifying management and ensuring consistency. This command displays details for each profile, including segment-specific isolation settings.

##  Arguments (optional)
| Argument | Description |
|---|---|
| none | This command does not take any arguments. |

##  Example usage
```
example_com:velocli> debug --profile_dump
[
  {
    "DE2E Isolation ON Segments": "",
    "Isolation ON Segments": "",
    "Profile Id": "55aeb5a8-d849-11ec-bbe4-0ae26eaf7805"
  }
]
```

##  Field descriptions
| Column | Description |
|---|---|
| DE2E Isolation ON Segments | Lists the segment IDs where Dynamic Edge to Edge (DE2E) isolation is enabled. DE2E isolation prevents Edges within these segments from dynamically forming tunnels with each other, even if traffic policies would normally allow it. An empty string indicates no specific segments are configured for DE2E isolation at the profile level. |
| Isolation ON Segments | Lists the segment IDs where general network isolation is enforced. This can restrict communication between segments or within a segment based on the profile configuration. An empty string indicates no specific segments are configured for general isolation at the profile level. |
| Profile Id | The unique identifier for the configuration profile. |